/* eslint-disable  func-names */
/* eslint-disable  no-console */

const Alexa = require('ask-sdk-core');

const GetNewFactHandler = {
  canHandle(handlerInput) {
    const request = handlerInput.requestEnvelope.request;
    return request.type === 'LaunchRequest'
      || (request.type === 'IntentRequest');
  },
  handle(handlerInput) {
    const factArr = data;
    const factIndex = Math.floor(Math.random() * factArr.length);
    const randomFact = factArr[factIndex];
    const speechOutput = GET_FACT_MESSAGE + randomFact;

    return handlerInput.responseBuilder
      .speak(speechOutput)
      .withSimpleCard(SKILL_NAME, randomFact)
      .getResponse();
  },
};

const HelpHandler = {
  canHandle(handlerInput) {
    const request = handlerInput.requestEnvelope.request;
    return request.type === 'IntentRequest'
      && request.intent.name === 'AMAZON.HelpIntent';
  },
  handle(handlerInput) {
    return handlerInput.responseBuilder
      .speak(HELP_MESSAGE)
      .reprompt(HELP_REPROMPT)
      .getResponse();
  },
};

const ExitHandler = {
  canHandle(handlerInput) {
    const request = handlerInput.requestEnvelope.request;
    return request.type === 'IntentRequest'
      && (request.intent.name === 'AMAZON.CancelIntent'
        || request.intent.name === 'AMAZON.StopIntent');
  },
  handle(handlerInput) {
    return handlerInput.responseBuilder
      .speak(STOP_MESSAGE)
      .getResponse();
  },
};

const SessionEndedRequestHandler = {
  canHandle(handlerInput) {
    const request = handlerInput.requestEnvelope.request;
    return request.type === 'SessionEndedRequest';
  },
  handle(handlerInput) {
    console.log(`Session ended with reason: ${handlerInput.requestEnvelope.request.reason}`);

    return handlerInput.responseBuilder.getResponse();
  },
};

const ErrorHandler = {
  canHandle() {
    return true;
  },
  handle(handlerInput, error) {
    console.log(`Error handled: ${error.message}`);

    return handlerInput.responseBuilder
      .speak('Sorry, an error occurred.')
      .reprompt('Sorry, an error occurred.')
      .getResponse();
  },
};

const SKILL_NAME = 'Haiku Reader';
const GET_FACT_MESSAGE = 'I have a haiku for you: ';
const HELP_MESSAGE = 'You can say tell me a haiku...  or, you can say stop... What can I help you with?';
const HELP_REPROMPT = 'You can ask me to tell a haiku or exit to stop. What can I help you with?';
const STOP_MESSAGE = 'Goodbye!';

const data = [
  `One deep breath inwards.
  Then let everything in go.
  Watch thoughts now fading`,

  `Okay now, you say.
  You are in your quiet place.
  You are safe here now`,
  
  `Are you here with me?
  Yes, count to three seven three.
  Three in... seven out... three`,
  
  `In in in in in.
  Out out out out out out out.
  In in in in in`,
  
  `Fill your lungs with air.
  You are the one in control.
  No one else but you`,
  
  `Listen - notice the sounds.
  Sounds of life surrounding you
  What are you hearing?`,
  
  `Close your eyes for now.
  This moment is yours to keep.
  No one can take it`,
  
  `Stop - pause - a moment,
  It's okay to put it down
  Let the tension go`,
  
  `What is true for you?
  What thoughts are you thinking of?
  Grounded in the now`,

  `Grounded in the now.
  Your breaths anchoring you here.
  In the present now.`
];

const skillBuilder = Alexa.SkillBuilders.custom();

exports.handler = skillBuilder
  .addRequestHandlers(
    GetNewFactHandler,
    HelpHandler,
    ExitHandler,
    SessionEndedRequestHandler
  )
  .addErrorHandlers(ErrorHandler)
  .lambda();
