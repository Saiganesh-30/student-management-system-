let students=JSON.parse(localStorage.getItem('students')||'[]');
function save(){localStorage.setItem('students',JSON.stringify(students));}
function addStudent(){let n=name.value.trim(),r=roll.value.trim();if(!n||!r)return alert('Fill all fields');students.push({n,r});save();name.value='';roll.value='';render();}
function del(i){students.splice(i,1);save();render();}
function render(){let q=(search.value||'').toLowerCase();list.innerHTML='';students.forEach((s,i)=>{if(s.n.toLowerCase().includes(q)||s.r.toLowerCase().includes(q)){list.innerHTML+=`<tr><td>${s.n}</td><td>${s.r}</td><td><button onclick='del(${i})'>Delete</button></td></tr>`}})}
render();