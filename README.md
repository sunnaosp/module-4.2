# module-4.2

Santiago workshop in API, 25-29 oktober.

We downloded postman and learnd how to use get, post, delete, patch and how to read the errors
200 it is ok, 400 error in the front and 500 error in the back (that is the simple way to explain it).

I learned alot this week, Santiago did live coding with us and gave us a few projects to do.
Here are some of the prodjects we needed to solve:

We needed to add the image to the js so it would points to the api server?
<img src="https://ecuaguia.com/iceland/images/${item.image}">

How to change the code so it will load img1 - img2- img3 instead of loading the same img over and over again?
After the loop in js we added: page = page + 1 and that fixed it.

Connect to the api, get the items and show the items in the drop down?

function show_results() {
document.querySelector("#results").style.display = "grid";
}

function hide_results() {
document.querySelector("#results").style.display = "none";
}

let my_timer;
function search() {
console.log("searching...");
document.querySelector("#results").innerHTML = "";
// const search = event.target.value
// console.log(search)
// Connect to the API
// clearTimeout
clearTimeout(my_timer);
my_timer = setTimeout(async () => {
const search = document.querySelector("#search_for").value;
const conn = await fetch(
`https://coderspage.com/iceland/search-items?search=${search}`
);
const data = await conn.json();
data.forEach((item) => {
let div_item = `<div id="ID${item.item_id}" class="result"> <span>${item.item_name}</span> <span>${item.item_id}</span> <span onclick="delete_item('${item.item_id}')">🗑️</span> </div>`;
document
.querySelector("#results")
.insertAdjacentHTML("afterbegin", div_item);
});
}, 500);
}

Connect to the API and send the ID as part of the url?

const conn = await fetch(`https://coderspage.com/iceland/item/${item_id}`, {
// mode: 'cors',
method: "DELETE",
headers: {
"Access-Control-Allow-Origin": "\*",
},
});
console.log("Item deleted from server");

// NOTE: Since you are all deleting, at some point
// there will be no items in the system. So don't panic

async function put_test() {
const conn = await fetch(`https://coderspage.com/iceland/put`, {
// mode: 'cors',
method: "PUT",
headers: {
"Access-Control-Allow-Origin": "\*",
},
});
console.log("PUT HERE");
}

put_test();

There were also few questions on the spot when the class was going on that is difficult to add to a readme file.
I missed out the first two days so i had all of the answers when i finaly got the time to catch up, but i learned alot by watching and reading through the code.
