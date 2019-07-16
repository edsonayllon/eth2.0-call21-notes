# Ethereum 2.0 Implementers Call 21 Notes

## Contents

<!-- TOC depthFrom:2 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Contents](#contents)
- [1 Meeting Details](#1-meeting-details)
- [2 Attendees](#2-attendees)
- [3 Agenda](#3-agenda)
	- [3.1 [Testing Updates](https://youtu.be/YB8o_5qjNBc?t=245)](#31-testing-updateshttpsyoutubeyb8o5qjnbct245)
		- [3.1.1 [Overflow in Slashing](https://github.com/ethereum/eth2.0-specs/pull/1286)](#311-overflow-in-slashinghttpsgithubcomethereumeth20-specspull1286)
		- [3.1.2 [Spec Freeze](https://github.com/ethereum/eth2.0-specs/pull/1242)](#312-spec-freezehttpsgithubcomethereumeth20-specspull1242)
		- [3.1.3 [Fuzzing](https://github.com/ethereum/eth2.0-specs/tree/dev/test_libs/pyspec/eth2spec/fuzzing)](#313-fuzzinghttpsgithubcomethereumeth20-specstreedevtestlibspyspeceth2specfuzzing)
	- [3.2 [Client Updates](https://youtu.be/YB8o_5qjNBc?t=830)](#32-client-updateshttpsyoutubeyb8o5qjnbct830)
		- [3.2.1 [Nimbus](https://github.com/status-im/nimbus)](#321-nimbushttpsgithubcomstatus-imnimbus)
		- [3.2.2 [Artemis](https://github.com/PegaSysEng/artemis)](#322-artemishttpsgithubcompegasysengartemis)
		- [3.2.3 [Trinity](https://github.com/ethereum/trinity)](#323-trinityhttpsgithubcomethereumtrinity)
		- [3.2.4 [Yeeth](https://github.com/yeeth)](#324-yeethhttpsgithubcomyeeth)
		- [3.2.5 [Harmony](https://docs.ethhub.io/ethereum-roadmap/ethereum-2.0/eth2.0-teams/harmony/)](#325-harmonyhttpsdocsethhubioethereum-roadmapethereum-20eth20-teamsharmony)
		- [3.2.6 [Lighthouse](https://github.com/sigp/lighthouse)](#326-lighthousehttpsgithubcomsigplighthouse)
		- [3.2.7 [Prysmatic](https://github.com/prysmaticlabs)](#327-prysmatichttpsgithubcomprysmaticlabs)
		- [3.2.8 [Lodestar](https://github.com/ChainSafe/lodestar)](#328-lodestarhttpsgithubcomchainsafelodestar)
		- [3.2.9 [Parity](https://github.com/paritytech/parity-ethereum)](#329-parityhttpsgithubcomparitytechparity-ethereum)
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

#### 3.1.1 [Overflow in Slashing](https://github.com/ethereum/eth2.0-specs/pull/1286)

**Danny Ryan**:
* Prysmatic Labs, Terence [Tsao], found an issue where the calculation and slashing was, due to the way it was formatted, potentially overflowing in a tester for `uint64`
* Relatively non-substantive changes (fixes, documentation, and things) in v08x branch [#1286](https://github.com/ethereum/eth2.0-specs/pull/1286). Includes a fix to this which alters the way the computation happens. Non-substantive, but doesn't overflow
* Seems relatively important so will get out v08x in the next few days (includes other minor things people have found).

#### 3.1.2 [Spec Freeze](https://github.com/ethereum/eth2.0-specs/pull/1242)

**Diederik Loerakker**
* Spec Freeze is over now, can stop throwing up to the spec and build.

**Danny Ryan**:
* Even after the Spec Freeze we will be expanding the coverage of the tests as needed.

#### 3.1.3 [Fuzzing](https://github.com/ethereum/eth2.0-specs/tree/dev/test_libs/pyspec/eth2spec/fuzzing)

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


#### 3.2.1 [Nimbus](https://github.com/status-im/nimbus)
**Mamy**:
* We launched our testnet 1, based on libp2p daemon, this morning
* We need to adapt the script, so that it starts with a single common because libp2p daemon is not built but it's almost done. Pretty soon by the end of the week.
* We are towards v0.8, all the small changes were integrated and right now a big focus is SSE
* We also started to align our State Transition function with PySpec in terms of naming
  * This is also to improve and facilitate testing
* We had significant parse improvement during the past week, accumulated 20 to 30x speed-up on the State Transition bench. We identified 3 bottlenecks:
  * In `process_crosslinks(...)` & `get_crosslinke_deltas(...)`. So both combined we had the 10x speed improvement
  * `get_crosslink_committee(...)` via caching, we improved by 2x the speed
* I can put or PR in the chat, so that if people are interested in seeing what we did, they can reproduce. Since we follow the spec-naming it should be very easy to navigate.
  * [Speed up process_crosslinks(...) and get_crosslink_deltas(...) by 10x - 15x in state_sim #314](https://github.com/status-im/nim-beacon-chain/pull/314)
  * [~2x state_sim speedup via additional caching in get_crosslink_committee #316](https://github.com/status-im/nim-beacon-chain/pull/316)
* We also published metrics library for Prometheus compact metrics:
  * [Nim metrics client library supporting the Prometheus monitoring toolkit](https://github.com/status-im/nim-metrics)
* We have a EWASM research library and we are very happy with. We have started a domain specific language in NIM that compiles to EWASM. It's quite competitive in terms of contract size:
  * [Nimplay is Domain Specific Language for writing smart contracts in Ethereum, using the Nim macro system](https://github.com/status-im/nimplay)
* Lastly on Ethereum 1, we had some connections issues that were resolved to Parity and Jeff.

#### 3.2.2 [Artemis](https://github.com/PegaSysEng/artemis)
**Jonny Rhea**:
* We've updated to there especially with the SSE
* Also been thinking about a tester slashings, computational requirements for the worst scenario
* We see the need to investigate the network load, you know from the attestations to decide what strategy to use when we're aggregating.
* That's the stuff we've been thinking about. Pretty much it.

#### 3.2.3 [Trinity](https://github.com/ethereum/trinity)
**Hsiao-Wei Wang**:
* Regarding specs Py SSE has been synced to v0.8 and the State Transition update is ongoing. I think it almost there thanks to Alex
* For the networking side, integrating with the Py library, we found some required issues that we need to fix on the upstream library.
* Also we are fixing some interoperability requirements and there is an insecure connections stake I'm posting here, I think Keven and maybe Raul will introduce it in the networking section. After the client update.
* That's the Trinity side, thank you.

#### 3.2.4 [Yeeth](https://github.com/yeeth)
**Dean Eigenmann**:
* I was doing some stuff with like the inter-op guys last week, I started helping out a bit on Artemis but handed that off again. So now I'm back on updating Yeeth to the latest spec version.

#### 3.2.5 [Harmony](https://docs.ethhub.io/ethereum-roadmap/ethereum-2.0/eth2.0-teams/harmony/)
**Mikhail Kalinin**:
* We've been pretty much working on an update to v0.8 spec, we're almost there, but SSE part is still in progress.
* We started to work on a slot clock mechanism, which is based on network-adjusted time proposed by Vitalik.
* We have a PR so far with basic implementation of that protocol. I'm going to take my time on that. Also we have started a small research to investigate into attestation aggregation strategies.
    * [Add draft spec for plaintext key exchange protocol #186](https://github.com/libp2p/specs/pull/186)
* The goal is to evaluate an approach that doesn't involve building additional overlays, like handle tree.
* Working on minimal libp2p or JVMs
* Worked on multistream implementation recently
* That's all from our side

#### 3.2.6 [Lighthouse](https://github.com/sigp/lighthouse)
**Adrian Manning**:
* Updating lighthouse to v0.8
* Have to re-optimize our tree-hash caching to include for more padding nodes
* Defining more extensive HTTP APIs which is working to improve dev experience
* Matt from ConsenSys building out some SSE partials into our codebase
* Slowly been testing an initial version of discovery v5 in small testnets
* Working towards standardizing a minimal libp2p for clients that are using libp2p
* In doing so we've had to update our RPC
    * In particular there's a discussion for the RPC to be using separate protocol IDs per request
* There's a PR where we try to standardize the basic libp2p implementation
    * [Libp2p Standardization Update #1281](https://github.com/ethereum/eth2.0-specs/pull/1281)
* That's it from us.

#### 3.2.7 [Prysmatic](https://github.com/prysmaticlabs)
**Raul Jordan**
* Caught up to v0.8, passing all spec tests
* Issues with Genesis trigger
* There's a lack of coverage for some spec test
    * Passed all SSE spec tests
    * Suprised that SSE failed in some Block sanity tests
* Reason was because the way Python converts the length mixing-length into bytes did not cover longer types of lengths.
* There was a list of values that were 512 in length. Encoded in Go gives different mixing length than in Python due to some edge cases, putting var ints.
* Having coverage for longer based lists can be good in SSE.
* Getting ready for optimizing Prism, code improvements, beautician testing, improvements to clients

#### 3.2.8 [Lodestar](https://github.com/ChainSafe/lodestar)
**Greg Markou**:
* Trying to upgrade to v0.8
* Began building dev tooling
* Separating out types exclusively so that in Javascript you can import Ethereum 2 types into a React project down in the future
    * Will help with providers, like a Web3.js provider.
* SSE almost up-to-date, ironing out bugs with Proto and Prism
* should be up-to-date on SimpleSerialize.com so that you guys can test it out online
* We're working towards ensuring that BLS works properly in-browser as well
    * Peculiar issues there will keep you updated
* Getting Herumi so that we can have some diversity in BLS
* In regards to the client, we comfortable to start doing Block production
* One we finish our update to v0.8, we'll start doing our testnet so that we can see how that plays out.
* Then getting that to work in-browser natively
* One the side: we also have assembly scripts, picking up now that we've frozen again, getting a bunch of native code so that we can execute WASM in some section for speedup of shuffling.
* See if we can convert SSE into purely assembly script for native WASM, seeing how that increases speed in the browser
* So getting ready to do dev-tooling, that's kinda where we're at
* Also, NIM, we're coming after you guys on the ERC20 contract, we'll get ya

#### 3.2.9 [Parity](https://github.com/paritytech/parity-ethereum)
**Wei Tang**:
* Finished the markolization library last week, hopefully, want to extend that into a caching library, but a few missing pieces.
* We're trying to update to v0.8 spec, issue we had was in the SSE which was quite a change
    * Now a lot more types that require configurable parameters
    * Wasn't expected because we were using a dynamic config
* Won't work for us. Will need to change our config structs to static types so we have all the type information at compile-time
* Large refactoring of the codebase



### 3.3 [Research Updates](https://youtu.be/YB8o_5qjNBc?t=1725)


### 3.4 [Network](https://youtu.be/YB8o_5qjNBc?t=2470)


### 3.5 [Spec Discussion](https://youtu.be/YB8o_5qjNBc?t=5095)


### 3.6 [Open Discussion/Closing Remarks](https://youtu.be/YB8o_5qjNBc?t=5540)
