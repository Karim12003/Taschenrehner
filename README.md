# Taschenrehner
window.alert("Alarm");
window.alert("Alarm!");
var ausgabe = document.getElementById("ausgabe");
var operator = null;
var ersteZahl = null;
var zweiteZahl = null;

for (var knopf of document.getElementById("zahlenfeld").children) {
  knopf.addEventListener("click", zahlEingabe.bind(this, knopf.textContent));
}
for (var knopf of document.getElementById("operatoren").children) {
  knopf.addEventListener("click", operatorEingabe.bind(this, knopf.textContent));
}

document.getElementById("gleich").addEventListener("click", ausrechnen);

document.getElementById("loescheAlles").addEventListener("click", loescheAlles);

document.getElementById("loescheAusgabe").addEventListener("click", loescheAusgabe);

function operatorEingabe(eingabe) {
  if (operator === null) {
    ersteZahl = Number(ausgabe.textContent);
    zweiteZahl = 0;
    ausgabe.textContent += eingabe;
  } else {
    ausgabe.textContent = ausgabe.textContent.replace(operator, eingabe);

  }
  operator = eingabe;
}

function zahlEingabe(eingabe) {
  if (ausgabe.textContent == 0 || zweiteZahl === 0) {
    ausgabe.textContent = eingabe;
    zweiteZahl = null;
  } else {
    ausgabe.textContent = ausgabe.textContent + eingabe;
  }
}

function ausrechnen() {
  if (operator !== null) {
    if (zweiteZahl === null) {
      zweiteZahl = Number(ausgabe.textContent);
    }
    switch (operator) {
      case "*":
        ausgabe.textContent = ersteZahl * zweiteZahl;
        break;
      case "/":
        if (zweiteZahl === 0) {
          ausgabe.textContent = "Mathematischer Fehler";
        } else {
          ausgabe.textContent = ersteZahl / zweiteZahl;
        }
        break;
      case "-":
        ausgabe.textContent = ersteZahl - zweiteZahl;
        break;
      case "+":
        ausgabe.textContent = ersteZahl + zweiteZahl;
        break;
      default:
        break;
    }
    operator = null;
    ersteZahl = null;
    zweiteZahl = 0;

  }
}

function loescheAlles()
{
	operator = null;
  ersteZahl = null;
  zweiteZahl = null;
  ausgabe.textContent=0;
}

function loescheAusgabe()
{
	if(ersteZahl!==null)
  {
  	zweiteZahl = 0;
  }
  else {
  	operator = null;
  }
  ausgabe.textContent = "0";
}