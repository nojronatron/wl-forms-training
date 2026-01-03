# README-1

## Purpose

Introduce the most basic Template file with as few elements as possible.

## Template Fields and Tags

Fields: Used to select message properties.

Tags: Capture content when the template is applied to a message.

## Type

The message type:

- Winlink: Winlink (RMS relay)
- P2P: Peer to peer
- RO: Radio ONly transmission

## To

Populates the message with whom the message is to be delivered to.

Can be:

- FCC Amateur Service callsign
- FCC SHARES Service callsign
- An internet email address

Limited by:

- Type: A P2P type message cannot be delivered to an internet address.

## Subj

Message subject.

## Msg

Text following this element defines the content for the message body.

Any template Fields and Tags that follow will end the Message Body text capture, allowing information to be appended after the `Msg:` body text.

## Install

Put the template file into one of the `Templates` folder:

- For all Winlink Express users: `Global Folders\Templates`
- For only one callsign: `Callsign\Templates`

## Use

1. Open Winlink Express.
2. Click 'New Message'
3. Click 'Select Template'
4. Click `hello-world-template.txt` in the Global (or callsign) directory.
5. Click the 'Select' button and the new Message will populate with values from the Template file.

## Resources

TemplateHelp.txt
