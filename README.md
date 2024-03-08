<!DOCTYPE html>
<html>
<head>
    <style>
        .quiz-container {
            width: 100%;
            max-width: 800px;
            margin: 0 auto;
        }
        .question {
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div class="quiz-container" id="quiz"></div>
    <button id="submit">Submit Quiz</button>
    <div id="results"></div>

    <script>
        const quizQuestions = [
            {
                question: "What is 2*5?",
                answers: {
                    a: "2",
                    b: "5",
                    c: "10"
                },
                correctAnswer: "c"
            },
            {
                question: "What is 3*2?",
                answers: {
                    a: "3",
                    b: "6",
                    c: "9"
                },
                correctAnswer: "b"
            }
        ];

        function showQuiz(questions, quizContainer){
            let output = [];
            let answers;

            for(let i=0; i<questions.length; i++){
                answers = [];
                for(letter in questions[i].answers){
                    answers.push(
                        '<label>'
                            + '<input type="radio" name="question'+i+'" value="'+letter+'">'
                            + letter + ': '
                            + questions[i].answers[letter]
                        + '</label>'
                    );
                }
                output.push(
                    '<div class="question">' + questions[i].question + '</div>'
                    + '<div class="answers">' + answers.join('') + '</div>'
                );
            }
            quizContainer.innerHTML = output.join('');
        }

        function showResults(questions, quizContainer, resultsContainer){
            let answerContainers = quizContainer.querySelectorAll('.answers');
            let userAnswer = '';
            let numCorrect = 0;

            for(let i=0; i<questions.length; i++){
                userAnswer = (answerContainers[i].querySelector('input[name=question'+i+']:checked')||{}).value;
                if(userAnswer===questions[i].correctAnswer){
                    numCorrect++;
                    answerContainers[i].style.color = 'lightgreen';
                }
                else{
                    answerContainers[i].style.color = 'red';
                }
            }
            resultsContainer.innerHTML = numCorrect + ' out of ' + questions.length;
        }

        showQuiz(quizQuestions, document.getElementById('quiz'));

        document.getElementById('submit').onclick = function(){
            showResults(quizQuestions, document.getElementById('quiz'), document.getElementById('results'));
        }
    </script>
</body>
</html>
