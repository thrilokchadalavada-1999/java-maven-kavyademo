package com.example;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@SpringBootApplication
@RestController
public class DemoApplication {

    public static void main(String[] args) {
        SpringApplication.run(DemoApplication.class, args);
    }

    @GetMapping("/")
    public String home() {

        return """
        <html>

        <head>

            <title>DevOps Project</title>

            <style>

                body {
                    text-align: center;
                    background-color: #f4f1f1;
                    padding-top: 20px;
                    margin: 0;
                    font-family: 'Trebuchet MS', 'Segoe UI', sans-serif;
                }

                h1 {
                    color: #222;
                    font-size: 50px;
                    margin-top: 10px;
                }

                .message {
                    margin-top: 40px;
                    color: #333;
                    width: 80%;
                    margin-left: auto;
                    margin-right: auto;
                    line-height: 1.9;
                    font-size: 30px;
                    font-weight: 500;
                }

                .top-icons {
                    font-size: 42px;
                }

                .bottom-icons {
                    font-size: 35px;
                    margin-top: 35px;
                    margin-bottom: 40px;
                }

                img {
                    width: 450px;
                    border-radius: 25px;
                    margin-top: 25px;
                    box-shadow: 0px 0px 18px gray;
                }

                hr {
                    width: 60%;
                    margin-top: 40px;
                    border: 1px solid #ccc;
                }

            </style>

        </head>

        <body>

            <div class='top-icons'>
                ✨ ⭐ ❤️ 💫 🌸 ✨
            </div>

            <h1>
                Welcome to My DevOps Project 🚀✨
            </h1>

            <img src='/images/Kavya199.png'>

            <hr>

            <div class='message'>

                This DevOps project was built with dedication,
                consistency and hard work 🚀❤️

                <br><br>

                You are part of my existence, part of myself and you are
                the reason I started this 💫✨

                <br><br>

                You are the living verse of life, a soul woven with wisdom,
                beauty, and grace ❤️⭐

                <br><br>

                May the Almighty bless you with strength
                to rise above every hardship, light to guide your path,
                and peace to dwell forever in your heart ✨🌸

                <br><br>

                May the love and blessings of your parents protect you always,
                nurturing your spirit and uplifting you in every step you take ❤️💫

            </div>

            <div class='bottom-icons'>
                ❤️ ✨ ⭐ 🌸 💫 ❤️
            </div>

        </body>

        </html>
        """;
    }
}
