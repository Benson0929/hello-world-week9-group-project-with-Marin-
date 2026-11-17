# GOLFAXY Controller Redesign

https://golfaxy.up.railway.app/

**Week 9 · Context and Evidence Study**  
**Benson & Marin**

## Project and audience

GOLFAXY is a golf game that uses a phone as a motion controller. Players hold the main control and turn their phone to aim, then release to lock the direction. To hit the ball, they hold again, swing the phone, and release once the swing is detected.

We designed for first-time players who look back and forth between their phone and the game screen. The controller should make it easy to see the current state, what to do next, and when to release.

## Shared design rules

| Element | Rule |
| --- | --- |
| **Typography** | Use the existing controller typeface. Set the main instruction in the blue control area to **60 px bold**, the short instructions below the screen heading to **20 px**, and secondary button labels to **16 px**. Use **14 px** for stage labels, sensor status messages, and safety notes. Use the same heading size and weight on both screens. |
| **Color** | Use the existing dark background and blue control area. Use bright blue when the player can act and muted blue when the player needs to wait. Show the state in text as well. |
| **Spacing** | Use consistent spacing between the screen heading and the instructions below it. Use **8 px** between a text field and the buttons below it, and **4–8 px** between adjacent buttons. |
| **Reusable component** | Both screens use the same large blue control area. Its largest text gives the player the action they can take now or tells them to wait. The heading describes the current state. The short instructions explain how to move the phone and when to release. |
| **Required behavior** | The first release locks the aim. A shot happens only after the player holds again, completes a valid swing, and releases. The player can aim again when the game is ready for the next shot. |
| **Flexible details** | Wording, icons, and the placement of supporting information can adapt to each screen. |
| **Must avoid** | Never prompt the player to take an action before it is available. For example, show “Hold to aim” again only when the game is ready for the next shot. |

## Our two redesigns

| Designer | Original screen | Redesign |
| --- | --- | --- |
| **Benson — Motion 1: Ready to Aim** | The heading reads “Hold to aim,” and the blue control repeats the instruction across two lines, “Hold” and “To aim.” A longer paragraph explains how to aim. | Change the heading to **“Ready to aim”** and combine the control text into one bold instruction, **“Hold to aim.”** Shorten the instructions to **“Turn left or right. Release to lock.”** and set them in **20 px**. |
| **Marin — Motion 2: Aim Locked** | The heading reads “Aim locked,” and the blue control splits the instruction into two lines, “Hold” and “To swing.” A longer paragraph explains when to swing and release. | Keep **“Aim locked”** as the heading and combine the control text into one bold instruction, **“Hold to swing.”** Shorten the instructions to **“Swing. Release when ‘Swing detected’ appears.”** and set them in **20 px**. |

**Ready to Aim — Before and After**

![Ready to Aim before and after](Ready%20to%20Aim%20before%20and%20after.png)


**Aim Locked — Before and After**

![Aim Locked before and after](Aim%20Locked%20before%20and%20after.png)

## A/B test with Claude

We tested whether Claude would keep the first available action on the main control and put later steps in the supporting text. For each screen, we used the same redesigned mockup and prompt in two separate chats. We attached Rules A in the first chat and Rules B in the second.

- [Rules A PDF](Rules%20A%20PDF.pdf) describes the main control as showing the action available now or telling the player to wait.
- [Rules B PDF](Rules%20B%20PDF%20.pdf) explicitly says to put the first available action on the main control and later steps in the supporting text.

### Benson — Ready to Aim

**Prediction before running B:** I predict that Claude will keep “Hold to aim” as the main control label and leave the turning and release instructions in the supporting text.

**Prompt used in both chats:**

> I’m redesigning the GOLFAXY phone controller for first-time players. The attached screen shows the “Ready to aim” state, before the player has pressed the main control.
>
> Using the attached screen and shared design rules, suggest one label for the main blue control and one short line of supporting text. Use the existing aiming interaction described in the rules.
>
> Return exactly two lines, labeled “Main control” and “Supporting text.”

| Version | Main control | Supporting text | Result |
| --- | --- | --- | --- |
| **A** | Hold to aim | Turn left or right. Release to lock. | **Pass** |
| **B** | Hold to aim | Turn left or right, then release to lock your aim. | **Pass** |

Both responses kept “Hold to aim” on the main control and put turning and releasing in the supporting text. Version B used “then” to make the sequence more explicit. The mockup already showed the intended label, so these results show that Claude preserved it under both versions of the rule.

### Marin — Aim Locked

**Prediction before running B:** The main control should say “Hold to swing,” and the supporting text should tell the player to release once the swing is detected.

**Prompt used in both chats:**

> Using the attached “Aim Locked” screen and shared design rules, suggest a label for the main blue control and one short line of supporting text for a first-time player who has locked their aim and is ready to swing.
>
> Follow the existing swing interaction and return exactly two lines labeled “Main control” and “Supporting text.”

| Version | First response | Result |
| --- | --- | --- |
| **A** | The main control told the player to hold to swing, and the supporting text explained when to release. | **Pass** |
| **B** | The main control still told the player to hold to swing, with the release instruction in the supporting text. | **Pass** |

Both responses followed the shared rule for the Aim Locked screen. The main control communicated that the player should hold to swing, and the supporting text explained when to release.

## Human observation and design decisions

**Benson:** I separated the state heading from the action label so that “Ready to aim” tells the player where they are and “Hold to aim” tells them what to do. I shortened the supporting instructions and increased their size to 20 px. When Marin played the original game, she paired her phone successfully but had trouble finding “Enable motion sensors” because it looked like the other secondary buttons. Her feedback reinforced the importance of making the next action easy to spot. In my Ready to Aim redesign, I kept “Hold to aim” as the most prominent text and placed the turning and release instructions in the supporting text.

**Marin:**Marin:** I played the original game and was able to pair my phone, but I had trouble finding the “Enable motion sensors” button because it looked like the other secondary controls. I suggested making it more prominent and added spacing guidelines for text fields and adjacent buttons to our shared rules. I also tested the redesigned “Aim Locked” screen with both versions of the rules. Both passed, and I recommend keeping “Hold to swing” as the main instruction and the release cue in the supporting text.

**AI contribution:** Claude generated button labels and supporting text using the redesigned screens and our shared rules. We compared the first responses from both rule versions.

**Open question:** Can a first-time player tell when to release while looking back and forth between the phone and the game screen?
