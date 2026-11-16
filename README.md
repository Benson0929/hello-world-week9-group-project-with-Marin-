# GOLFAXY Controller Redesign

https://golfaxy.up.railway.app/

**Week 9 · Context and Evidence Study**  
**Benson Chuang & Marin**

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

![Ready to Aim before and after](images/ready-to-aim-before-after.png)

**Aim Locked — Before and After**

![Aim Locked before and after](images/aim-locked-before-after.png)

## A/B test with Claude

We tested whether Claude would keep the first available action on the main control and put later steps in the supporting text. For each screen, we used the same redesigned mockup and prompt in two separate chats. We attached Rules A in the first chat and Rules B in the second.

- [Rules A PDF](docs/golfaxy-rules-a.pdf) describes the main control as showing the action available now or telling the player to wait.
- [Rules B PDF](docs/golfaxy-rules-b.pdf) explicitly says to put the first available action on the main control and later steps in the supporting text.

### Benson — Ready to Aim

**Prediction before running B:** [Paste the prediction you recorded before the second test.]

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

**Prediction before running B:** [Paste Marin’s recorded prediction.]

**Prompt used in both chats:** [Paste Marin’s actual prompt.]

| Version | First response | Result |
| --- | --- | --- |
| **A** | [Paste Marin’s first Claude response for Rules A.] | **Pass** |
| **B** | [Paste Marin’s first Claude response for Rules B.] | **Pass** |

Both responses followed the shared rule for the Aim Locked screen. The main control communicated that the player should hold to swing, and the supporting text explained when to release.

## Human observation and design decisions

**Benson:** I separated the state heading from the action label so that “Ready to aim” tells the player where they are and “Hold to aim” tells them what to do. I shortened the supporting instructions and increased their size to 20 px. [Add who tried the screen, what they did or said, and what you decided to keep or change based on that observation.]

**Marin:** [Add Marin’s own design or testing contribution, who tried the screen, what they did or said, and what she decided to keep or change.]

**AI contribution:** Claude generated button labels and supporting text using the redesigned screens and our shared rules. We compared the first responses from both rule versions.

**Open question:** Can a first-time player tell when to release while looking back and forth between the phone and the game screen?
