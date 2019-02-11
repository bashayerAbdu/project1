module.exports = (robot) => {
  const mes = ['Hi', 'Hello', 'hola'] 
  //
 robot.respond(`/${mes.join('|')}/i`, (res) => {
  res.send(res.random(mes))
 });

  robot.hear(/hubot I need some advice/, function(res) {
    let responses = ["Think before you speak.","Everything in moderation, including moderation.","Just because you don't know what you want yet, it doesn't mean that there's nothing to want.- Emily Henry", 
    "“The best way to predict your future is to create it.”- Abraham Lincoln", "Rule of life. If you bother to ask someone’s advice, then bother to listen to it.- Sophie Kinsella" ]
    let rand = Math.floor(Math.random() * responses.length)
    return res.send(`${responses[rand]}`);
  });

//print text 
  robot.respond(/show my (.*) pic or (.*)/i, (res) => {
   let pic1= [
      "https://media.giphy.com/media/QSu9dboSacWxq/giphy.gif",
      "https://media.giphy.com/media/xlVa9n9q75eoM/giphy.gif",
      "https://media.giphy.com/media/i6hceabbnshnW/giphy.gif",
    "https://media.giphy.com/media/zZQe7wglGKCEE/giphy.gif"]

    let pic2= ["https://media.giphy.com/media/l0ExbqkAKqIrlWdI4/giphy.gif",
	  "https://media.giphy.com/media/fiIbvD2CtW6ru/giphy.gif",
	  "https://media.giphy.com/media/CPutABwbvXC92/giphy.gif"]

    const lovepic = res.match[1]
    const lovepic2 = res.match[2]
    if (lovepic === 'beautiful' || 'elegant'){
   res.reply(res.random(pic1)); // res.send(res.random())
   return
    }
    
   if (lovepic2 === 'sun shin'|| 'sun rise'){
   res.reply(res.random(pic2)); // res.send(res.random())
   return
    }
    res.reply('no pic for ${lovepic} or ${lovepic2}')
  });
// print imeg 
 
  //
 
   ///////////////my own way 
   robot.respond(/is it (workday||schoolday)/i, function(res){
    var today = new Date();

    res.reply(today.getDay() === 0 || today.getDay() === 6 ? "YES" : "NO");
}); //see the date and print accurt in it 

robot.router.post('/hubot/chatsecrets/:room', (req, res) => {
    const room = 'UFZ724A6L'
    const data = JSON.parse(req.body.payload)
     const secret = data.secret
  
   robot.messageRoom(room, `I have a secret: ${secret}`)
  //
    res.send('OK')
  })

  let = setIntervalId = null
   //
    robot.respond(/what time is it now?/, (res) => {
      res.send('time:')
      setIntervalId = setTimeout (), (res) => {
        let date1 = new Date 
        let time = date1.toLocaleTimeString()
      res.send(time)
      return
    }
    })
   //
    robot.respond(/stop timer/, (res) => {
     if (!setIntervalId) {
      clearTimeout(setIntervalId)
       setIntervalId = null
    setTimeout (() =>   res.send('Not annoying you right now, am I?'), 60 *100)
      return
    }
  })} /// ecpect to print cureent time and clear it 


hubot --adapter slack
  /////HUBOT_SLACK_TOKEN=xoxb-545040400103-544184113909-kRMU5dtkWqCtOeTDcNce1mv3 bin/hubot --adapter slack/
