let text = " howw youuuu He unaffected sympathize discovered at no am conviction principles Girl ham very how yet hill four show Meet lain on he only size Branched learning so subjects mistress do appetite jennings be in Esteems up lasting no village morning do offices Settled wishing ability musical may another set age Diminution my apartments he attachment is entreaties announcing estimating And total least her two whose great has which Neat pain form eat sent sex good week Led instrument sentiments she simplicity";//random text from google
let arr = text.split(" ");//create an array of random words
let random = Math.floor((Math.random() * arr.length) + 1);//picks a random number that represent random word
let randomword = arr[random];//random word for the game
let wordlen = arr[random].length;// define length of of word
let arrword = randomword.split('');//defind array of the chosen random word by letters
let count = 0;//define a counter
let password = [];
for (i = 0; i < wordlen; i++) {
    password.push('*');    //create password  represented with "*,*,*"  long as the random word
}


for (j = 0; j < 11; j++) {// user has max 10 attempts
    if (j === 10) {
        console.log("game over")
        break; // if user guesses worng 10 attempts game over
    }
    //if user gusses the word in less of 10 attempts
    if (count === wordlen) {     //  counter gets to number of letters
        console.log('you win the word is " ' + randomword + ' "')  // and wins the game
        break;
    }
    // user gets instructions
    //user could guess only one letter from a-z per try

    var try1 = [];
    try1 = prompt('you have left ' + (10 - j) + ' guesses. guess one letter only and discover the word ' + password);
    let guess1 = /[a-z,A-Z]/i.test(try1) && try1.length == 1;
    while (!guess1) {                    // if users guess is not one letter                
        try1 = prompt("invalid! only one letter from a-z please"); // he gets invalid messege
        guess1 = /[a-z,A-Z]/i.test(try1) && try1.length == 1;     //another check  if guess is a letter
    }                                                         // to get out of while loop
    for (i = 0; i < wordlen; i++) {  //going threw letteres and check
        if (arrword[i] === try1) {  // check if guess is correct
            let replace = password.splice(i, 1, try1);// replacing * with correcrt letter guesses  
            count += 1; //counting to end the game if guessing the password
        }
    }
}