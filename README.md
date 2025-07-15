
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>TestXperience</title>
  <style>
    body {
      font-family: sans-serif;
      background: #f4f4f4;
      margin: 0;
      padding: 0;
    }
    header {
      background: #003566;
      color: white;
      text-align: center;
      padding: 20px;
    }
    section {
      padding: 20px;
      max-width: 800px;
      margin: auto;
    }
    h2 {
      color: #003566;
    }
    button {
      margin: 5px;
      padding: 10px 15px;
      background: #1982c4;
      color: white;
      border: none;
      cursor: pointer;
      border-radius: 4px;
    }
    pre {
      background: black;
      color: lime;
      padding: 10px;
      margin-top: 10px;
      height: 100px;
      overflow-y: auto;
    }
    form input, form select {
      margin: 5px 5px 10px 0;
      padding: 8px;
      width: calc(100% - 20px);
      display: block;
    }
    #bugList li {
      background: #fff;
      margin: 10px 0;
      padding: 10px;
      border-left: 5px solid #ef476f;
      list-style: none;
      box-shadow: 0 1px 3px rgba(0,0,0,0.1);
}
    #bugList button {
      background: #ef476f;
      margin-top: 5px;
    }
  </style>
</head>
<body>
  <header>
    <h1>TestXperience</h1>
    <p>Automation Testing Demo + Bug Tracker</p>
  </header>

  <section id="automation">
    <h2>Automation Showcase</h2>
    <button onclick="runTest('Login')">Run Login Test</button>
    <button onclick="runTest('Signup')">Run Signup Test</button>
    <button onclick="runTest('Checkout')">Run Checkout Test</button>
    <pre id="consoleOutput">Console Output...</pre>
  </section>

  <section id="bug-tracker">
    <h2>Bug Tracker</h2>
    <form id="bugForm">
      <input type="text" id="title" placeholder="Bug Title" required />
      <input type="text" id="desc" placeholder="Description" required />
      <select id="priority">
        <option>Low</option>
        <option>Medium</option>
        <option>High</option>
      </select>
      <button type="submit">Add Bug</button>
    </form>
    <ul id="bugList"></ul>
  </section>

  <script>
    function runTest(type) {
      const output = document.getElementById("consoleOutput");
      output.textContent = Running ${type} test... ✅\n~ Designed by Nagacharan R;
    }

    document.getElementById("bugForm").addEventListener("submit", function (e) {
      e.preventDefault();
 const title = document.getElementById("title").value;
      const desc = document.getElementById("desc").value;
      const priority = document.getElementById("priority").value;

      const bug =  title, desc, priority ;
      let bugs = JSON.parse(localStorage.getItem("bugs")) || [];
      bugs.push(bug);
      localStorage.setItem("bugs", JSON.stringify(bugs));
      displayBugs();
      this.reset();
    );

    function displayBugs() 
      const bugList = document.getElementById("bugList");
      const bugs = JSON.parse(localStorage.getItem("bugs")) || [];
      bugList.innerHTML = ”;
      bugs.forEach((bug, index) => 
        const li = document.createElement("li");
        li.innerHTML = `<strong>{bug.title}</strong> (bug.priority)<br>{bug.desc}
                        <br><button onclick="deleteBug(${index})">Delete</button>`;
        bugList.appendChild(li);
      });
    }

    function deleteBug(index) {
      let bugs = JSON.parse(localStorage.getItem("bugs")) || [];
      bugs.splice(index, 1);
      localStorage.setItem("bugs", JSON.stringify(bugs));
      displayBugs();
    }

    displayBugs();
  </script>
</body>
</html>
