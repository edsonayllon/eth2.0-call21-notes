# Ethereum 2.0 Implementers Call 21 Notes

## Contents

<!-- TOC depthFrom:2 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Contents](#contents)
- [1 Meeting Details](#1-meeting-details)
- [2 Attendees](#2-attendees)
- [3 Agenda](#3-agenda)
	- [3.1 [Testing Updates](https://youtu.be/YB8o_5qjNBc?t=245)](#31-testing-updateshttpsyoutubeyb8o5qjnbct245)
		- [3.1.1 Potential Overflow](#311-potential-overflow)
		- [3.1.2 Spec Freeze](#312-spec-freeze)
		- [3.1.3 Fuzzing](#313-fuzzing)
	- [3.2 [Client Updates](https://youtu.be/YB8o_5qjNBc?t=830)](#32-client-updateshttpsyoutubeyb8o5qjnbct830)
	- [3.3 [Research Updates](https://youtu.be/YB8o_5qjNBc?t=1725)](#33-research-updateshttpsyoutubeyb8o5qjnbct1725)
	- [3.4 [Network](https://youtu.be/YB8o_5qjNBc?t=2470)](#34-networkhttpsyoutubeyb8o5qjnbct2470)
	- [3.5 [Spec Discussion](https://youtu.be/YB8o_5qjNBc?t=5095)](#35-spec-discussionhttpsyoutubeyb8o5qjnbct5095)
	- [3.6 [Open Discussion/Closing Remarks](https://youtu.be/YB8o_5qjNBc?t=5540)](#36-open-discussionclosing-remarkshttpsyoutubeyb8o5qjnbct5540)

<!-- /TOC -->


## 1 Meeting Details

- **Meeting Date-Time:** Thursday 2019/7/11 at [14:00 GMT](http://www.timebie.com/std/gmt.php?q=14)
- **Meeting Duration:** 1.5 hours
- **[Youtube Livestream](https://www.youtube.com/watch?v=YB8o_5qjNBc)**

## 2 Attendees

- [Adrian Manning](https://github.com/AgeManning)
- [Alex Stokes](https://github.com/ralexstokes)
- [Ben Edgington](https://github.com/benjaminion)
- [Benjamin Burns](https://github.com/benjamincburns)
- [Carl Beekhuizen](https://github.com/CarlBeek)
- [Cem Ozer](https://github.com/cemozerr)
- [Daniel Ellison](https://github.com/zigguratt)
- [Dankrad Feist](https://github.com/dankrad)
- [Danny Ryan](https://github.com/djrtwo)
- [Dean Eigenmann](https://github.com/decanus)
- [Diederik Loerakker](https://github.com/protolambda)
- [Dmitriy Ryajov](https://github.com/dryajov)
- [Greg Markou](https://github.com/GregTheGreek)
- [Hsiao-Wei Wang](https://github.com/hwwhww)
- [Jacek Sieka](https://github.com/arnetheduck)
- [Jannik Luhn](https://github.com/jannikluhn)
- [John Adler](https://media.consensys.net/@adlerjohn)
- [Jonny Rhea](https://github.com/jrhea)
- JosephC
- [Joseph Delong](https://github.com/dangerousfood)
- [Justin Drake](https://github.com/JustinDrake)
- [Kevin Main-Hsuan Chia](https://github.com/mhchia)
- [Leo Bautista Gomez](https://github.com/leobago)
- [Luke Anderson](https://github.com/spble)
- [Mamy Ratsimbazafy](https://github.com/mratsim)
- [Matt Garnett](https://github.com/c-o-l-o-r)
- [Mike Goelzer](https://github.com/mgoelzer)
- [Mikhail Kalinin](https://github.com/mkalinin)
- [Musab Alturki](https://github.com/malturki)
- [Nicholas Lin](https://www.linkedin.com/in/nicholas-lin-50267ba3/)
- [Nicolas Liochon](https://github.com/nkeywal)
- [Paul Hauner](https://github.com/paulhauner)
- [Preston](https://github.com/prestonvanloon)
- [Raul Jordan](https://github.com/rauljordan)
- [Raúl Kripalani](https://github.com/raulk)
- [Steven Schroeder](https://github.com/schroedingerscode)
- [Trenton Van Epps](https://medium.com/@trenton.v)
- [Vitalik Buterin](https://vitalik.ca/)
- [Wei Tang](https://github.com/sorpaas)
- [Whiteblock](https://github.com/Whiteblock)
- [Will Villanueva](https://medium.com/@william.j.villanueva)
- [Zak Cole](https://github.com/zscole)

## 3 Agenda

### 3.1 [Testing Updates](https://youtu.be/YB8o_5qjNBc?t=245)

#### 3.1.1 Potential Overflow

**Danny Ryan**:
* Prysmatic Labs, Terence [Tsao], found an issue where the calculation and slashing was, due to the way it was formatted, potentially overflowing in a tester for `uint64`
* Relatively non-substantive changes (fixes, documentation, and things) in `v08x` branch [#1286](https://github.com/ethereum/eth2.0-specs/pull/1286). Includes a fix to this which alters the way the computation happens. Non-substantive, but doesn't overflow
* Seems relatively important so will get out `v08x` in the next few days (includes other minor things people have found).

#### 3.1.2 Spec Freeze

**Diederik Loerakker**
* Spec Freeze is over now, can stop throwing up to the spec and build.

**Danny Ryan**:
* Even after the Spec Freeze we will be expanding the coverage of the tests as needed.

#### 3.1.3 Fuzzing

**Justin Drake**:
* Goal: Basic Fuzzing infrastructure for all the clients.
    * Client implementers don't have to worry too much about being compliant with the State Transition Function.
    * You can spend most of your time on what makes a client "a client": Networking, Databases, and what-not.
* We've started with pySpec and the goal executable specs.
* I think the next target for integration will be Lighthouse. Hopefully, a lot of the infrastructure will be generic for clients.
* Might come in the next two weeks, hopefully.

**Danny Ryan**:
* We'll go the experiment round with one and learn some things.
* Any other testing things before we move on?

**Diederik Loerakker**:
* We are Fuzzing v0.8.0 and Go excludes post-spec is almost up-to-date now, pySpec already is.
* It's really up to the hosts, as the first clients, to also be on the same spec version. Ain't gonna start so soon.

**Jacek Sieka**:
* About the Fuzzing, how do you drive it? Like how is the Fuzzing driven, what is the input?

**Diederik Loerakker**:
* The problem with Fuzzing is that we have 2 kinds of inputs:
    1. States
    2. Blocks
* The State itself is easily randomized. It contains script traffic contents. It has several validity assumptions.
* You can have any kind of Block, these are like the attack vector. So you're Fuzzing blocks now and you're extending at seconds corpora echoes of the pre-state.
* You could say we are mostly focusing on Blocks now.
* They are looking to make this extension of the State more intelligent so that you could make more progress in a chain test review of more different pre-states being Fuzzed.

**Jacek Sieka**:
* What's the difference between that and the YAML file?

**Danny Ryan**:
* YAML files are particularly constructed tests
* Given a pre-state and given some input that we want to hit certain conditions, certain bounds:
    * Maybe a normal path
    * Maybe testing right on the boundary
    * Testing past the boundary
* These are particularly constructed tests, something you might write in your own test feed.
* Whereas these (Fuzzing) are taking pre-states and modifying blocks generally at random, within some sort of bounds, and just applying them to test things that we weren't necessarily thinking about.
* Does that make sense?

**Paul Hauner**:
* Yeah, I'm not exactly sure how the Ethereum Foundation one works but I know May's explained how our one works
  1. You start with a valid block or some valid object that kind of reaches as far into code path as it can
  2. Then the Fuzzer meters all your code
  3. Then it randomizes the fields of the original object you gave it
  4. Then detects if it explores new code paths
- It smartly tries to expand itself out to cover as much code as it can by deterministically, but somewhat randomly, modifying the object and learning about how that affected the coverage.

**Mamy**:
* Okay, yeah, because the Fuzzing, that proto outline, seemed like it didn't check the bit patterns of the code path that were exercised by the framework.

**Diederik Loerakker**:
* Yeah, simplifying it a little bit here but, yeah
* The randomization of the Block is done by let for sure and that checks the coverage and then tries to randomize as best it could. Just the parts that improve coverage.
* And again, you don't want to first only run pre-states, it's more complicated than that.

**Justin Drake**:
* Yeah it'd definitely coverage driven and there's the randomization aspect.

**Danny Ryan**:
* Cool, any other questions on this before we move in?
* Preston has a question:
    * "How does the Fuzz harness look: is it libfuzz or is this new tool compatible?"

**Preston**
* Hey, I think Proto (Diederik Loerakker) just answered that he said that it would be using libfuzz to, basically, you give the signal feedback: did you get farther through the test or was this the worst fuzzing scenario?
* So that answers the question, thanks.

**Diederik Loerakker:**
* Some people here are already libfuzz's libfuzzer
* We have Peter working on this with lots of experience with it and extending it
* What I was just saying about these 2 different kinds of states we're working on. We have the Beacon States and the Block
* We don't want to involve only the block inputs because if you're always Fuzzing the same states, you don't get the same coverage as you could if you're Fuzzing multiple states
* So this why we're trying to improve on the normal architecture
* Yet it's somewhat similar to libfuzz service since this is what's being used internally

**Justin Drake**:
* Did he suggest that the current approach was good enough at exploring many different paths and finding bugs.
* I think the main limit was the speed of PyStack, that you couldn't Fuzz that much, it would be rather slow.
* Hopefully once we do differential Fuzzing on the Lighthouse, we'll get a bit more confidence.

**Diederik Loerakker:**
* We get a lot of poor performance because of spec and hopefully also with clients.
* I think with PySpec is that there are these functions that are not pleasant outs they all inefficiently repeat themselves, not precomputing anything
* Now in the next Go spec updates, I optimize, precompute this, precompute that, so we get half, almost client speed spec.
* I tried to keep this portable.

**Danny Ryan**:
* One of the paths might be to differentially Fuzz against the Go spec and the clients and then if we find issues, to then go back to the Py spec and make sure we agree with what the functionality should be.
* We'll keep everyone updated about Fuzzing over the coming weeks.


### 3.2 [Client Updates](https://youtu.be/YB8o_5qjNBc?t=830)


### 3.3 [Research Updates](https://youtu.be/YB8o_5qjNBc?t=1725)


### 3.4 [Network](https://youtu.be/YB8o_5qjNBc?t=2470)


### 3.5 [Spec Discussion](https://youtu.be/YB8o_5qjNBc?t=5095)


### 3.6 [Open Discussion/Closing Remarks](https://youtu.be/YB8o_5qjNBc?t=5540)
