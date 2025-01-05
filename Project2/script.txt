// Jose Alberto Tayag, 000907201
// February 16,2024

// Wait until the webpage is fully loaded.
window.addEventListener("load", function () {
  // Retrieve buttons from there ids.
  const g1_q1_button = document.getElementById("g1_q1_button");
  const g1_q2_button = document.getElementById("g1_q2_button");
  const g2_q1_button = document.getElementById("g2_q1_button");
  const g2_q3_button = document.getElementById("g2_q3_button");
  const g3_q2_button = document.getElementById("g3_q2_button");
  g1_q1_button.addEventListener("click", group_1_choice_1);
  g1_q2_button.addEventListener("click", group_1_choice_2);
  g2_q1_button.addEventListener("click", group_2_choice_1);
  g2_q3_button.addEventListener("click", group_2_choice_3);
  g3_q2_button.addEventListener("click", group_3_choice_2);
});
/**
 * evaluating the user's input against specific criteria.
 * It parses the input as an integer, checks if it's not a number, and then determines if it falls
 * within a defined range, setting the output message accordingly.
 */
function group_1_choice_1() {
  let value = parseInt(document.getElementById("g1_q1_input").value);
  let result = "";

  if (isNaN(value)) {
    result = "Not a number";
  } else if (value === 0 || (value >= 13 && value <= 17)) {
    result = "In Range";
  } else {
    result = "Out of Range";
  }

  document.getElementById("g1_q1_output").innerHTML = result;
}
/**
 * Converts the user's input from days into years, months, and days. It checks for negative or non-numeric
 * input and calculates the corresponding time span, updating the result.
 */
function group_1_choice_2() {
  let value = parseFloat(document.getElementById("g1_q2_input").value);
  let years;
  let months;
  let days;
  let result;

  if (isNaN(value) || value <= 0) {
    result = "Negative Input!!!";
  } else {
    years = Math.floor(value / 365.25); // Calculate years
    console.log(years);
    let remainingDays = value % 365.25; // Calculate remaining days
    console.log(remainingDays);
    months = Math.floor(remainingDays / 30); // Calculate months
    console.log(months);
    days = remainingDays % 30.44; // Calculate days
    console.log(days);
    let daysConvert = days.toFixed(2);
    result = `${years} Years, ${months} Months, ${daysConvert} Days`;
  }

  document.getElementById("g1_q2_output").innerHTML = result;
}
/**
 * Identifies whether the user's input is a vowel, a special case, or not a vowel.
 * It converts the input to lowercase and uses a switch statement to set the result.
 */
function group_2_choice_1() {
  let value = document.getElementById("g2_q1_input").value;
  let toLowerValue = value.toLowerCase();
  let result = "";

  switch (toLowerValue) {
    case "a":
    case "e":
    case "i":
    case "o":
    case "u":
      result = "A Vowel";
      break;
    case "y":
      result = "Sometimes";
      break;
    default:
      result = "Not a vowel";
  }
  document.getElementById("g2_q1_output").innerHTML = result;
}
/**
 * Calculates the factorial of the user's input. Validates the input to ensure it's a positive integer
 * before performing the calculation, and updates the result or an error message.
 */
function group_2_choice_3() {
  let value = parseInt(document.getElementById("g2_q3_input").value);
  let total = 1;
  let result = "";

  if (isNaN(value) || value <= 0) {
    result = "Cannot compute factorial value";
  } else {
    for (let i = 1; i <= value; i++) {
      total *= i;
    }
    result = total;
  }

  document.getElementById("g2_q3_output").innerHTML = result;
}
/**
 * identifies the operation to perform,
 * and calculates the result. It handles addition, subtraction, multiplication, division, and modulus
 * operations, updating the result or an error message if the input is invalid.
 */
function group_3_choice_2() {
  let value = document.getElementById("g3_q2_input").value.trim();
  let operator = "";
  let operand1 = "";
  let operand2 = "";

  for (let i = 0; i < value.length; i++) {
    if (
      value[i] === "+" ||
      value[i] === "-" ||
      value[i] === "*" ||
      value[i] === "/" ||
      value[i] === "%"
    ) {
      operator = value[i];
      operand1 = value.substring(0, i).trim();
      operand2 = value.substring(i + 1).trim();
      break;
    }
  }

  if (
    operand1 === "" ||
    operand2 === "" ||
    operator === "" ||
    isNaN(parseInt(operand1)) ||
    isNaN(parseInt(operand2))
  ) {
    document.getElementById("g3_q2_output").innerHTML = "Invalid Formula";
    return;
  }

  operand1 = parseInt(operand1);
  operand2 = parseInt(operand2);

  let result;
  switch (operator) {
    case "+":
      result = operand1 + operand2;
      break;
    case "-":
      result = operand1 - operand2;
      break;
    case "*":
      result = operand1 * operand2;
      break;
    case "/":
      result = operand1 / operand2;
      break;
    case "%":
      result = operand1 % operand2;
      break;
    default:
      result = "Invalid formula";
  }

  document.getElementById("g3_q2_output").innerHTML = result;
}
