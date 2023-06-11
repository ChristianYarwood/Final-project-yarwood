const express = require('express');
const app = express();
const p4module = require('./p4-module');

app.get('/cit/question', (req, res) => {
  const questions = p4module.getQuestions();
  const response = {
    error: '',
    statusCode: 200,
    questions: questions
  };
  res.json(response);
});

app.get('/cit/answer', (req, res) => {
  const answers = p4module.getAnswers();
  const response = {
    error: '',
    statusCode: 200,
    answers: answers
  };
  res.json(response);
});

app.get('/cit/questionanswer', (req, res) => {
  const qas = p4module.getQuestionsAnswers();
  const response = {
    error: '',
    statusCode: 200,
    questions_answers: qas
  };
  res.json(response);
});

app.get('/cit/question/:number', (req, res) => {
  const number = req.params.number;
  const question = p4module.getQuestion(number);
  if (!question) {
    const response = {
      error: 'Question not found',
      statusCode: 404
    };
    res.status(404).json(response);
  } else {
    const response = {
      error: '',
      statusCode: 200,
      question: question,
      number: number
    };
    res.json(response);
  }
});

app.get('/cit/answer/:number', (req, res) => {
  const number = req.params.number;
  const answer = p4module.getAnswer(number);
  if (!answer) {
    const response = {
      error: 'Answer not found',
      statusCode: 404
    };
    res.status(404).json(response);
  } else {
    const response = {
      error: '',
      statusCode: 200,
      answer: answer,
      number: number
    };
    res.json(response);
  }
});

app.get('/cit/questionanswer/:number', (req, res) => {
  const number = req.params.number;
  const qa = p4module.getQuestionAnswer(number);
  if (!qa) {
    const response = {
      error: 'Question and Answer not found',
      statusCode: 404
    };
    res.status(404).json(response);
  } else {
    const response = {
      error: '',
      statusCode: 200,
      question: qa.question,
      answer: qa.answer,
      number: number
    };
    res.json(response);
  }
});

app.get('*', (req, res) => {
  const response = {
    error: 'Route not found',
    statusCode: 404
  };
  res.status(404).json(response);
});

app.listen(3000, () => console.log('Server running on port 3000'));
