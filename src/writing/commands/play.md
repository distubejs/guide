---
description: This page is a follow-up and bases on the code of the main page.
---

# Play command

::: tip Events
This command will emit `playSong`, `playList`, `addSong`, and `addList` events.
:::

With [`distube.play()`](https://distube.js.org/DisTube.html#play) method, your bot will join a voice channel and play song from the url or YouTube based on the top match for the string given.

:::: tabs
::: tab Play Command
```javascript
if (command === 'play') {
	distube.play(message, args.join(' '))
}
```
:::

::: tab Message Listener
```javascript
client.on('message', message => {
	if (!message.content.startsWith(prefix) || message.author.bot) return

	const args = message.content.slice(prefix.length).trim().split(' ')
	const command = args.shift().toLowerCase()

	if (command === 'ping') {
		message.channel.send('Pong!')
	}
	if (command === 'play') {
		distube.play(message, args.join(' '))
	}
})
```
:::
::::

Now your bot can play music when you are in a voice channel and send `!play a random song name` message. To reply the command, you should listen to [DisTube events](../listening-to-distube-events/) to know exactly the song and queue properties.

