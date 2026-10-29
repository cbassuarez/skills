# Example: `/deepen write an artist statement for my MFA thesis show, an 8-channel sound installation about the LA river`

Unedited output from a headless run (`claude -p`).

---

**Field:** I've framed this the way a sound-art curator would write exhibition wall text. Your committee and your visitors will both read the statement standing next to the work. So it gets judged on whether it matches what they hear, not on how it reads in a seminar.

**a. What a top curator would do that you're not asking for**
- **Only claim what can be heard.** Before writing anything, stand at the entrance with a timer and note what you hear in the first 60 seconds, and from which speaker. Cut any sentence a visitor can't check by listening.
- **Make the 8 channels mean something.** Say in one sentence what the speakers map to: points along the river's 51 miles, a cross-section of the channel, upstream to downstream, or something else. If you can't write that sentence, the spatial layout isn't carrying meaning yet. Better to find out now than at the opening.
- **Pin down which river.** Name the stretches you recorded (Glendale Narrows, Sepulveda Basin, the downtown concrete channel, the Long Beach estuary), plus the dates and how much water was flowing. A dry-season trickle and a storm surge are different pieces.
- **Place the work against direct precedents by name.** The obvious ones are Annea Lockwood's *A Sound Map of the Hudson River* (1982) and Bill Fontana's *River Sounding* (2010). Locally, Lewis MacAdams founded Friends of the LA River (FoLAR) as an art action in 1986. Your committee will be thinking of these, so you should be able to say in one sentence what your piece does that they don't.
- **Settle the ethics before writing.** Do any recordings include people living along the river, and did they consent? Name Tongva land only if the piece actually engages with it. Otherwise leave it out rather than adding it as boilerplate.

**b. Rawest material**
- **Your channel map, DAW session and the gallery's speaker plot,** instead of a description of the piece. Only you have these.
- **Your field-recording log** (site, date, time, mic type: hydrophone, contact mic or air mic), plus USGS stream-gauge flow readings for those dates (waterdata.usgs.gov). These replace "the river" in general and my memory of it.
- **A timed listen in the installed room,** with notes at 0:00, 0:30 and 1:00 from three positions. This replaces what the piece is supposed to sound like. Only you can do this.
- **Your rough studio notes, proposal and crit feedback,** instead of drafts already written in statement voice. Only you have these.
- **Primary sources for river history:** Army Corps of Engineers channelization records and Gumprecht's *The Los Angeles River: Its Life, Death, and Possible Rebirth*, instead of Wikipedia. Listen to the precedent recordings themselves, not descriptions of them.

**c. Methods and tools**
- **Timed listen from three positions:** gives the statement a factual core.
- **Beverly Serrell's "big idea" test (*Exhibit Labels*):** one sentence that every other line has to serve.
- **Claim-to-evidence table:** each sentence gets a row naming the recording, speaker or log entry that backs it. A sentence with no row gets cut.
- **Rule & Levine's "International Art English" (Triple Canopy, 2012) as a strike list:** "interrogates," "liminal," "invites the viewer," abstract nouns made from verbs. Add a river list: "forgotten river," "concrete scar," "nature reclaiming," the movie references.
- **Read-aloud test:** read it at gallery volume next to the running piece. It should take 90 seconds or less.

**d. What would show it's right (not you, not me)**
- **Cold-visitor test.** Three people who haven't heard the piece or talked to you about it spend five minutes in the room, then read the statement. **Passes if** at least 2 of 3 can point to the sound or speaker the central sentence describes, and none of them names something the statement promised that the room didn't deliver.
- **River-insider read.** Someone from FoLAR, an LA River Ranger, or someone who lives on the stretch you recorded reads it. **Passes if** they flag no factual or ethical misstatements about the place.
- **Fact check.** Every historical or flow claim is checked against USGS, Army Corps records or Gumprecht. **Passes at** zero mismatches.

**Rewritten prompt**
```text
I need an artist statement for my MFA thesis show: an 8-channel sound installation about the Los Angeles River. It's for [wall text / handout / thesis document — I'll tell you which]. Either way it will be read in the room next to the work, so it has to be true to what a visitor actually hears.

Don't start from what you know about the LA River. Start from my material. If I haven't given you any of these, ask me for them instead of filling in from general knowledge:
1. My channel map: what plays on each of the 8 speakers, where each one sits in the room, how long the piece is and whether it loops.
2. My recording log: which stretches of the river, dates, how much water was flowing, and which mics (hydrophone, contact mic on concrete, air mics). Also whether any recordings include people's voices, and whether those people consented.
3. A timed listen: what I hear in the first 60 seconds at the entrance, then from the center and from a corner.
4. My rough notes, proposal and crit feedback, in the words I used before I started trying to sound like a statement.
5. My program's requirements: word limit and format.

Then work in this order:
1. Before drafting, give me two one-sentence answers. First, what the 8 channels map to (places along the river, a cross-section of the channel, time, something else). Second, what this piece does that Annea Lockwood's "A Sound Map of the Hudson River" and Bill Fontana's "River Sounding" don't. If you can't get either answer from my material, stop and tell me. That would be a gap in the piece or in my explanation, and I need to know before the show.
2. Write the big idea as one sentence (Serrell's test), built from those two answers.
3. Draft the statement. Lead with what the visitor hears and where. Bring in river history only where a specific sound needs it. Stay within my word limit (200 words if I haven't given one), and keep it readable aloud in under 90 seconds.
4. Make a claim-to-evidence table: each sentence gets a row naming the recording, speaker or log entry that backs it. Cut any sentence that has no row.
5. Strip International Art English (Rule & Levine): "interrogates," "liminal," "invites the viewer," abstract nouns made from verbs. Also strip river clichés: "forgotten river," "concrete scar," "nature reclaiming," movie references.
6. Check every historical or flow claim against USGS stream-gauge data, Army Corps records or Gumprecht's history of the river, not against memory. Mention Tongva land or people living along the river only if the piece actually engages them, and only in terms my recording log supports.

Finish with a script for a test I'll run. Three people who haven't heard the piece or talked to me about it spend five minutes in the room, then read the statement. They're asked what the river was doing in the piece, and which sound or speaker the central sentence refers to. It passes if at least 2 of 3 point to the right sound and none of them names a claim the room didn't deliver. Separately, someone who works on the river (FoLAR, an LA River Ranger or a local resident) reads it, and it passes if they find no factual or ethical misstatement about the place. Tell me exactly what to ask and what counts as a fail. When I bring back the results, revise the statement based on them, and tell me plainly if it failed.
```

I can run this now if you send the channel map and recording log first. Next time, `/deepen --go` runs the rewrite straight away.
