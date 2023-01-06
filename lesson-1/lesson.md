# Lesson 1: Getting started with Sonic Pi

For the first lesson, we'll consider what a computer is. There are many video resources to draw on but the key points to emphasise are
that a computer takes an input, process it and provides output. Allow learners to keep coming back to this.

## Learning Objectives

- Know that there are many different types of computing devices.
- Understand how a computer uses a sequence of statements to do something, and that this sequence is called a program.
- Be able to give the computer instructions so that output is heard in the form of Sonic Pi music.

## Lesson Summary

- An introduction to the basic physical parts of a Raspberry Pi
- A demonstration that the Raspberry Pi can behave like a traditional computer
- A group exercise to act out a simple program
- Starting the Sonic Pi application
- The first music program

## Starter

Ask learners to define what a computer might be and more specifically, where they have seen or used computers before. As they come up with ideas, ask them to identify characteristics that are true of all the examples.

Start the demo code below, play it for a moment or two and explain that in a few weeks the students will be able to make computers do this for themselves. Emphasise that they'll be free to do what they want with it and have a lot of fun in the process; programming is about getting the computer to do exactly what you want it to do. It's not important for the students to see the application or any code at this stage, just for them to hear the sounds coming from the computer.

```ruby
use_debug false

live_loop :low do |idx|
  #  idx = 0
  synth :zawa, wave: 1, invert_wave: 1, phase: 0.25, release: 5, note: :e1, cutoff: (range 60, 120, 10)[idx]
  sleep 4
  idx += 1
end

live_loop :lands, auto_cue: false do |idx|
  use_synth :dsaw
  use_random_seed 66679
  with_fx :reverb, room: 1  do
    16.times do
      ns = (scale :e2, :minor_pentatonic, num_octaves: 3)
      play ns.choose, detune: 12, release: 0.1, amp: 2, amp: rand + 0.5, cutoff: rrand(70, 120)
      sleep 0.125
    end
  end
end

live_loop :bikes do |idx|
  sleep 0.25
  sample :guit_em9, rate: -1
  sleep 7.75
end

live_loop :time, auto_cue: false do |idx|
  sample :bd_haus, amp: 2.5
  sleep 0.5
end

```

## Main Development

1. Split the class into groups again and give each group a deck of the [computer program cards](files/Lesson-1-computer-program-cards.pdf). Ask each group to take out the statement cards and the control card from the deck. Then ask each group to form a line and to give each member of the group a statement card after shuffling them. The person at the start of the line should be given the control card. Explain that the person holding the control card should carry out the instructions on the statement card, and then pass the control card to the next person in the line like a relay baton. When the control card has reached the end of the line, they should stop. This should be repeated for a number of random orderings, after which the groups could be invited to create their own orderings. A helpful analogy might be cooking, where collections of statements are recipes and the control flow is which stage of the recipe you're at.

2. Start the Sonic Pi software. First, invite the students to log into their Raspberry Pi and start the graphical environment. It might help to display instructions on how to achieve this on a projector for all to see.

3. Explain to them that they can use the same statements on the cards in the computer program: `play` and `sleep`. Invite them to spend the remaining time writing their own programs and listening to the results.

4. Before the end of the lesson be sure to reflect on what has been learnt.

## Plenary

Groups should be invited to choose card orderings for other groups to act out. Following this, a discussion should be held about how this relates to a computer. A computer works by executing statements one after another in a specific order. A given order of statements is called a **program**. Each program executes with a given **control flow**; this describes which statement we are executing and what the next statement will be.

## Homework

Students should be asked to invent statements of their own which they could act out with their family using the [Programming Statement Worksheet](files/Lesson-1-Statement-Worksheet.pdf).
