---
layout: post
title:  "Weighted Average Calculator"
date:   2020-08-28 16:30:00 -0700
categories: Coding
tags : C# Calculator
---

{% highlight ruby %}
using System;
using static System.Console;

namespace WeightedAverageCalc
{
    class WAC
    {
        static void Main(string[] args)
        {
            // constant weights are defined here
            const float ASSIGNMENTS_PERCENTAGE = 0.2f;
            const float MIDTERM_EXAM_PERCENTAGE = 0.3f;
            const float QUIZ_PERCENTAGE = 0.1f;
            const float FINAL_EXAM_PERCENTAGE = 0.3f;

            // variables for storing the grades of a student
            float assignments;
            float midtermExam;
            float quiz1;
            float quiz2;
            float finalExam;

            float weightedExams = 0;
            float totalWeightedAverage = 0;


            Title = "CSIS1175 - Assignment 3 - By SoheeKim";

            DisplayBanner("Total Weighted Average Calculator");

            Console.Write("\n");
        

            // The user enters the grades, the program gets them and stores them in the corresponding variable

            bool isAssignmentValid, isMidtermValid, isQuiz1InputValid, isQuiz2InputValid, isFinalInputValid;

            isAssignmentValid = GetUserInput("Assignments", 0, 100, out assignments);
            isMidtermValid = GetUserInput("Midterm Exam", 0, 100, out midtermExam);
            isQuiz1InputValid = GetUserInput("Quiz1", 0, 100, out quiz1);
            isQuiz2InputValid = GetUserInput("Quiz2", 0, 100, out quiz2);
            isFinalInputValid = GetUserInput("Final Exam", 0, 100, out finalExam);

            if (isAssignmentValid && isMidtermValid && isQuiz1InputValid && isQuiz1InputValid && isQuiz2InputValid && isFinalInputValid == true)
            {

                String assignmentsGrade, midtermExamGrade, quiz1Grade, quiz2Grade, finalExamGrade, averageLetterGrade;


                assignmentsGrade = LetterGrade(assignments);
                midtermExamGrade = LetterGrade(midtermExam);
                quiz1Grade = LetterGrade(quiz1);
                quiz2Grade = LetterGrade(quiz2);
                finalExamGrade = LetterGrade(finalExam);

                

                // Total Weighted Avergae is sum of products of grades and their weight
                totalWeightedAverage += WeightedGrade(assignments, ASSIGNMENTS_PERCENTAGE);
                totalWeightedAverage += WeightedGrade(midtermExam, MIDTERM_EXAM_PERCENTAGE);
                totalWeightedAverage += WeightedGrade((quiz1 + quiz2), QUIZ_PERCENTAGE);
                totalWeightedAverage += WeightedGrade(finalExam, FINAL_EXAM_PERCENTAGE);
                averageLetterGrade = LetterGrade(totalWeightedAverage);


                Console.Write("\n\n");
                

                DisplayTableRow("Assessment", "Percentage", "Your Grade");
                DisplayTableRow("--------------", " -----------", "------------");

                DisplayTableRow("Assignments", ASSIGNMENTS_PERCENTAGE, assignments, assignmentsGrade);
                DisplayTableRow("MidTerm Exam", MIDTERM_EXAM_PERCENTAGE, midtermExam, midtermExamGrade);
                DisplayTableRow("Quiz1", QUIZ_PERCENTAGE, quiz1, quiz1Grade);
                DisplayTableRow("Quiz2", QUIZ_PERCENTAGE, quiz2, quiz2Grade);
                DisplayTableRow("Final Exam", FINAL_EXAM_PERCENTAGE, finalExam, finalExamGrade);

                WriteLine("------------------------------------------");

                // change the following line of code such that the Floor value of totalWeightedAverage is displayed on Console
                DisplayTableRow("Weighted Total", 1, (float)Math.Floor(totalWeightedAverage), averageLetterGrade); //** Change only this line **//

                WriteLine("\n");

                weightedExams += WeightedGrade(midtermExam, MIDTERM_EXAM_PERCENTAGE);
                weightedExams += WeightedGrade((quiz1 + quiz2), QUIZ_PERCENTAGE);
                weightedExams += WeightedGrade(finalExam, FINAL_EXAM_PERCENTAGE);
                weightedExams /= 0.8f;

                // change the following line of code such that the Ceiling value of weightedExams is displayed on Console
                WriteLine("The Weighted Average Total on Exams (Midterm, Quizzes, Final exam) is {0:F2} ({1})", (float)Math.Ceiling(weightedExams),averageLetterGrade); //** Change only this line **//
                WriteLine("If WAT-on-Exams is less than 50, the student fails the course.");

            }

            
                
            

        }


        static bool GetUserInput(string textMessage, byte min, byte max, out float userInputValue)
        {


            string userInput;
            bool isInputValid;

            Write("Enter a value for " + textMessage + ":");

            userInput = ReadLine();
            isInputValid = float.TryParse(userInput, out userInputValue);



            if (isInputValid == false)
            {

               
                WriteLine("!!!");
                WriteLine("The value for"+ textMessage +"must me a number!");
                WriteLine("!!!");

                WriteLine("\n Press a key to quit...");
                ReadKey();


                //userInputValue = 0;
                return false;


            }

            else if (userInputValue < min || userInputValue > max)
            {



                WriteLine("!!!");
                WriteLine("The value for" + textMessage + "must me a number between 0 and 100 inclusive!");
                WriteLine("!!!");

                WriteLine("\n Press a key to quit...");
                ReadKey();


                //userInputValue = 0;
                return false;

            }

            else
            {
                return true;

            }
        }

         static string LetterGrade(float grade)
        {
            string lettergrade;
            

            if (grade >= 95.0)
                lettergrade = "A+";
            else if (grade >= 90.0)
                lettergrade = "A";
            else if (grade >= 85.0)
                lettergrade = "A-";
            else if (grade >= 80.0)
                lettergrade = "B+";
            else if (grade >= 75.0)
                lettergrade = "B";
            else if (grade >= 70.0)
                lettergrade = "B-";
            else if (grade >= 65.0)
                lettergrade = "C+";
            else if (grade >= 60.0)
                lettergrade = "C";
            else if (grade >= 55.0)
                lettergrade = "C-";
            else if (grade >= 50)
                lettergrade = "D";
            else
                lettergrade = "F";

            return lettergrade;

        }


    static void DisplayBanner(string text)
        {
            Console.Write("\\***********************************************\\\n");
            Console.Write("\\\t\t\t\t\t\t\\\n");
            Console.Write("\\\t{0}\t\\\n",text);
            Console.Write("\\\t\t\t\t\t\t\\\n");
            Console.Write("\\***********************************************\\\n");
        }

        static void DisplayTableRow(string th1, string th2, string th3)
        {
            
            WriteLine("{0,13}{1,14:P0}{2,14}", th1, th2, th3);
        }

        static void DisplayTableRow(string names, float constpercentages, float grades, string lettergade)
        {
            WriteLine("{0,14}{1,14:P0}   {2,-8:f2}{3,-1}", names, constpercentages, grades, lettergade);
        }

        static float WeightedGrade(float userGrades, float userPercentages)
        {
            return userGrades * userPercentages;
        }


        //  your method definitions are written here (out of Main method). A method cannot be defined inside another method
    }
}
{% endhighlight %}

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
