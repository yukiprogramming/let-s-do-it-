# let-s-do-it-main
package com.example.yuki.letsdoit;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

import android.view.View.OnClickListener;
import android.view.View;


public class MainActivity extends AppCompatActivity {
    private int currentQuestion;
    private String [] questions;
    private String [] answers;
    private Button answerButton;
    private Button questionButton;
    private TextView questionView;
    private TextView answerView;
    private EditText answerText;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        init();

    }
    public void init() {
        questions = new String[]{"In which city was the Titanic built?",
                "Which country sent its navy around the world to fight the Japanese in 1904?","How many rings on the Olympic flag?",
        "What colour is vermilion a shade of?","Which US state is named on the label of a Jack Daniels bottle?","Air Lingus is the national airline of which country?",
        "Who is the director of the Lord of Rings trilogy?","Which chess piece can only movie diagonally? ","Which country’s men use the most deodorant?","What is the white trail behind a jet plane made from? "};
        answers = new String[]{"Belfast","Russia","Five","Red","Tennessee","Republic of Ireland","Peter Jackson ","Bishop","Japan","Ice Crystals"};
        currentQuestion = -1;
        answerButton = (Button)findViewById(R.id.AnswerButton);
        questionButton = (Button)findViewById(R.id.QuestionButton);
        questionView = (TextView) findViewById(R.id.QuestionTextView);
        answerView = (TextView) findViewById(R.id.AnswerTextView);
        answerText = (EditText) findViewById(R.id.AnswerText);
        answerButton.setOnClickListener(new OnClickListener(){
            @Override
            public void onClick(View v) {
                checkAnswer();
            }});
        questionButton.setOnClickListener(new OnClickListener(){
            @Override
            public void onClick(View v) {
                showQuestion();
            }});
    }


    public void showQuestion()
    {
        currentQuestion++;
        if(currentQuestion == questions.length)
            currentQuestion =0;
        questionView.setText(questions[currentQuestion]);
        answerView.setText("");
        answerText.setText("");
    }

    public boolean isCorrect(String answer)
    {
        return (answer.equalsIgnoreCase(answers[currentQuestion]));
    }

    public void checkAnswer()
    {
        String answer = answerText.getText().toString();
        if(isCorrect(answer))
            answerView.setText("You're right!");
        else
            answerView.setText("Sorry, the correct answer is "+answers[currentQuestion]);
    }





}
