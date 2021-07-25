let board = document.querySelector("#board");
let data = [];
let turn = "black";

for (let i = 0; i < 25; i++) {
    data[i] = [];
    for (let j = 0; j < 25; j++) {
        data[i][j] = 0;
    }
}

data.forEach(function (rowdata, i) {
    let row = document.createElement("div");
    row.className = "row";
    rowdata.forEach((_, j) => {
        let cell = document.createElement("div");
        cell.setAttribute("class", "cell");
        cell.setAttribute("row", i);
        cell.setAttribute("col", j);
        cell.onclick = click;
        row.append(cell);
    })
    board.append(row);
})

function click(e) {
    let p = document.createElement("div");
    let currentrow = e.target.getAttribute("row")
    let currentcol = e.target.getAttribute("col")
    if (turn == "black") {
        p.id = "circle1"
        data[currentrow][currentcol] = "black"
        checker(currentrow,currentcol)
        turn = "white"
    } else {
        p.id = "circle2"
        data[currentrow][currentcol] = "white"
        checker(currentrow,currentcol)
        turn = "black"
    }

    e.target.append(p);
    
}

function checker(currentrow,currentcol) {
    if(data[currentrow][currentcol] == turn){
        
        let count = 0;
        for(let i = -5 ; i < 5; i++){
            console.log(+currentcol + i, data[currentrow][currentcol+i] == turn)
            if(data[currentrow][+currentcol + i ] == turn){
                count++
                console.log(currentrow, currentcol+i, "에 더해짐 총 ", count)
            }
        }
        if (count >= 5){
            alert("승리")
        }
    }
}


function rowline() {
    
}

function colline() {

}

function dialine() {

}

function dedialine() {

}
------------------------------------------------------------------------------------------

<!DOCTYPE html>
<html lang="ko">

<head>
    <title>
        오목!
    </title>


    <style>
        .row {
            display: flex;
        }

        .cell {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 25px;
            min-width: 25px;
            border: 1px solid black;
        }

        #circle1 {
            background-color: black;
            width: 23px;
            height: 23px;
            border-radius: 100%;
        }

        #circle2 {
            background-color: white;
            width: 19px;
            height: 19px;
            border-radius: 100%;
            border: 2px solid black;
        }
    </style>
</head>

<body>
    <div id="board">

    </div>
    <script src="./omock.js" type="text/javascript">
    </script>
</body>

</html>
