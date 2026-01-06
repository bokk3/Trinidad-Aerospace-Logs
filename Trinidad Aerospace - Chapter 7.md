# Chapter Seven: Night Shift

**[T.A.I. Personnel File #2847 - Emergency Operations Log]**  
**Date: August 28, 2043**  
**Time: 10:47 PM - 04:33 AM**  
**Incident Code: PROMETHEUS-VAL-083**

---

The call came at 10:30 PM Saturday night.

I was home, trying to sleep before the Monday departure, when my new T.A.I.-issued phone buzzed. Not my regular phone—this one was encrypted, registered to a shell company, and only had contacts for other T.A.I. personnel.

Dr. Lal's name on the screen.

"Hello?"

"We have a problem." His voice had none of its usual enthusiasm. Just tension. "Can you come in? Now?"

"What kind of problem?"

"The kind where we either fix it tonight or we don't make the Tobago window. Dr. Ramcharan is calling in everyone. We're running an emergency validation test."

I was already pulling on clothes. "I'll be there in twenty minutes."

"Fifteen would be better."

I made it in thirteen, pushing the Subaru harder than I should have through empty Saturday night streets. The hidden garage was busier than I'd ever seen it—six vehicles, including Dr. Ramcharan's sedan and what looked like Wrench's pickup truck.

Colonel Thompson was at his security station, looking more alert than usual. "Straight through. They're in the development lab."

The tunnel felt different at night. The lighting was the same, but the absence of any ambient noise from the city above made every footstep, every water drip echo louder. The facility at night was its own world, completely disconnected from the sleeping city.

The elevator deposited me onto a main floor that was anything but sleeping. Every light was on. People were moving with purpose between workstations. And coming from the development lab, I could hear raised voices.

I found Dr. Lal, Gabi, Maya, Raj, and Wrench clustered around a monitor showing data that looked bad even to my relatively inexperienced eye. Pressure spikes, unstable oscillations, things that made the simulation graphs look like a seismograph during an earthquake.

"What happened?" I asked.

"Final validation burn," Gabi said without looking away from the screen. "We ran a ten-second test with substitute propellant—can't risk metallic hydrogen for ground testing. Everything was fine for eight seconds. Then this." She pointed to where the graphs went chaotic. "Combustion instability. The chamber pressure started oscillating, frequency increasing, until we had to emergency shutdown."

"We've run this same test profile twenty times," Dr. Lal said, frustration clear in his voice. "Never had this problem. But if we can't figure out what caused it, we can't risk a full test in Tobago with actual metallic hydrogen. An instability like this with real propellant could be catastrophic."

Dr. Ramcharan stood slightly apart from the group, arms crossed, watching the data with an expression I couldn't quite read. Not angry. Not panicked. Just intensely focused.

"Walk me through it," she said. "From the beginning. What changed?"

"Nothing," Gabi insisted. "Same engine configuration, same test stand, same procedures. Only difference is we'd just finished the disassembly and reassembly for transport prep. But we followed every checklist, verified every connection—"

"Show me the reassembly logs," Wrench interrupted. He'd been quiet until now, but his machinist's instinct was clearly telling him something.

Maya pulled up the documentation. Pages of checked boxes, signed-off procedures, measurements and verifications.

"Here," Wrench pointed. "Injector assembly. Who did the final torque check?"

"I did," one of the younger engineers said nervously. "Followed the spec exactly. 45 foot-pounds on all mounting bolts."

"And thermal cycling? After torque, you heat cycle it?"

"The spec doesn't call for—"

"The spec assume you're doing initial assembly," Wrench cut him off. "When you disassemble and reassemble, metal got stress memory. Bolts that were torqued, removed, then torqued again—they don't sit the same. Need to heat cycle to let everything settle into new equilibrium."

Dr. Lal was already pulling up thermal analysis models. "He's right. The injector face—if the bolt loading is even slightly non-uniform, it could cause micro-deflections in the combustion chamber. At high pressure, those deflections could create acoustic resonances—"

"Which would cascade into combustion instability," Maya finished. "The frequency we're seeing in the data matches a chamber resonance mode."

"So we heat cycle and retest?" Gabi asked.

"Not enough time," Dr. Ramcharan said. "Heat cycle takes six hours minimum to do properly. We need to leave for Tobago in seven hours. If we delay departure, we lose the weather window, tropical depression is forecast for midweek."

Everyone looked at each other. The weight of the moment was palpable. Months of work, millions of dollars, the first real test of metallic hydrogen propulsion—all potentially derailed by a bolt torque issue.

"There's another option," I heard myself say.

Everyone turned to look at me. Dr. Ramcharan raised an eyebrow.

"The control system," I continued, my mind racing through the simulations I'd been running all week. "We've been treating combustion instability as something to prevent. But what if we treat it like a drift?"

"Explain," Dr. Ramcharan said.

I moved to the workstation, pulling up the control algorithm code. "When you drift a car, you're not preventing the slide—you're managing an inherently unstable situation by making constant small corrections. The car wants to spin out, but you use throttle and steering to maintain controlled instability. The engine is the same—combustion wants to be unstable, but we can use injector valve timing and mixture ratios to keep it in a controlled state."

"We already do that," Gabi pointed out. "That's what the control system is for."

"Right, but look at the response time." I highlighted the relevant code. "The system is tuned to prevent instabilities from developing. It's conservative—waits for clear signals before making corrections. What if instead we tune it to actively manage instability? Predict and correct before the oscillations grow large enough to cascade?"

Dr. Lal was nodding slowly. "Increase the control loop frequency, reduce the correction threshold, use predictive algorithms instead of reactive ones..."

"Exactly. It's the same mathematics I use to predict drift angles before they fully develop. Read the early indicators—pressure gradients, temperature transients, flow rate fluctuations—and correct preemptively."

"That's aggressive," Maya said. "It could work, or it could make things worse. More corrections means more potential for introducing new instabilities."

"Or," Raj added, "it means we stay ahead of the problem instead of chasing it."

Dr. Ramcharan looked at the clock on the wall. 11:15 PM. "How long to implement this?"

"Two hours to modify the code," I estimated. "Another hour to test and validate in simulation. Then we'd need to load it to the engine controller and run an actual test burn."

"Four hours total. That gives us one hour of safety margin before we need to start loading trucks." She made a decision. "Do it. Dr. Lal, you supervise the code development. Maya, you run the simulations. Gabi, prep the test stand for another burn. Wrench, you and your team do a complete visual inspection of the engine while we're working on software—I want to be absolutely certain there are no other surprises."

"And if this doesn't work?" Gabi asked.

"Then we delay departure, lose the weather window, and try again next month." Dr. Ramcharan's expression was hard. "But I didn't build this facility to play it safe. We take the calculated risk. Get to work."

---

The next four hours were the most intense of my life.

Dr. Lal and I huddled over the code, modifying control algorithms that I'd spent all week learning. The challenge wasn't just making the changes—it was doing it correctly, understanding every consequence, ensuring we weren't introducing new failure modes.

"Here," Dr. Lal said, pointing at a section of code. "This is where we define the stability margin. Currently set at 15% deviation from nominal. What do you think?"

"Too conservative for active management. We need to operate closer to the edge. Maybe 5%?"

"That gives us very little safety margin."

"But it lets us correct smaller instabilities before they grow. Think of it like drift—you don't wait until you're 15 degrees off course to correct. You feel the car starting to slide and you're already adjusting."

He studied the code, running mental calculations. "You're right. But we need faster sensor sampling to support that. Increase the data acquisition rate to 10 kHz."

"Can the hardware handle that?"

"It better." He made the changes. "Maya, can you simulate this?"

Across the room, Maya was building test scenarios in her computational models. "Give me the updated parameters... okay, running it now."

We watched her screens as simulated burns played out. The first few showed promising results—the control system catching and correcting instabilities that would have cascaded in the original algorithm.

But the fifth simulation failed spectacularly. The engine went unstable in a different mode, one we hadn't anticipated.

"What happened there?" Dr. Lal demanded.

Maya rewound the data. "The faster correction rate created a feedback loop. The system overcorrected, which caused a new instability, which triggered another overcorrection. Classic control theory problem—too much gain."

"So we need to tune the correction magnitude," I said. "Not just how quickly we respond, but how strongly."

"Damping factor," Dr. Lal agreed. "We're treating this like a simple control problem, but it's actually a multi-mode dynamic system. Each instability mode needs different damping."

We dove back into the code. The clock ticked past midnight, then 1 AM. Coffee appeared—I'm not sure who brought it, but suddenly there were cups at every workstation. Someone ordered food. Doubles from a late-night spot, arriving in greasy paper bags that left oil stains on technical documents.

By 2 AM, we had a version that survived all of Maya's simulations. Every test case, every failure mode we could think of, handled smoothly. The control system was more aggressive, more responsive, but stable across the entire operating envelope.

"This is good," Maya said, reviewing the results. "I mean, it's radical and terrifying, but the mathematics work. If the hardware performs like the simulations suggest, this should handle the bolt torque issue and any other instabilities that develop."

"Time to find out," Gabi said. She'd been prepping the test stand in the restricted pressure chamber. Through the matted glass window, I could see the bright lights, the engine mounted and ready. "We're clear for a test burn. Ten seconds, 75% throttle, same profile as the failure run."

Dr. Ramcharan appeared from wherever she'd been—probably coordinating the backup plans if this didn't work. "Load the new control algorithm. Let's see if calculated risk pays off."

I uploaded the code to the engine controller, my hands surprisingly steady despite the exhaustion and adrenaline. Every line of code we'd written, every simulation Maya had run, every piece of theory Dr. Lal had taught me—it all came down to this.

"Upload complete," I confirmed. "Controller is running the new algorithm. All systems show green."

We moved to the control room adjacent to the pressure chamber. Banks of monitors, redundant safety systems, reinforced glass windows looking into the chamber where the engine waited. Gabi ran through the pre-test checklist with practiced efficiency.

"Ventilation system active. Pressure vessel sealed. Propellant tanks pressurized—substitute mixture, not metallic hydrogen. Ignition system armed. All personnel clear of the chamber."

Through the window, I could see the engine on its test stand. Sixty pounds of precisely machined metal and ceramic, connected to fuel lines and control systems, about to prove whether my intuition about control theory translated to rocket propulsion.

"Final checks," Gabi called out. "Dr. Lal, propulsion?"

"Go."

"Maya, computational?"

"Go."

"Wrench, mechanical?"

"Go."

"Blogger?" She looked at me.

Everyone was watching. Waiting. The control system was my responsibility now. If it failed, that failure would be mine.

"Go," I said.

Dr. Ramcharan nodded to Gabi. "Light it up."

"Initiating test sequence. T-minus ten seconds."

The countdown proceeded in my ears and on the displays. My eyes were fixed on the control system monitors, watching the algorithms initialize, seeing the system enter its active management state.

Three. Two. One.

Ignition.

The engine lit with a roar that was muted by the chamber walls but still loud enough to feel in your chest. Through the window, that impossibly bright exhaust plume formed, shorter and more focused than a conventional engine. The test stand shook. The chamber filled with light and heat and noise.

And the monitors showed... stability.

Combustion chamber pressure held steady at nominal. Temperature gradients within acceptable ranges. Flow rates balanced. The control system was working—making hundreds of tiny corrections per second, riding the edge of instability like I rode the edge of a drift, keeping everything balanced through constant microadjustments.

Two seconds. Four seconds. Six seconds.

Then I saw it. A small fluctuation in the pressure reading. Growing. The same pattern that had caused the failure earlier.

The control system caught it. Valve timing adjusted. Fuel mixture shifted. Temperature compensation applied. The fluctuation damped out before it could cascade.

"Did you see that?" Dr. Lal breathed. "It worked. The predictive algorithm caught the instability."

Eight seconds. Nine. Ten.

"Shutdown," Gabi commanded.

The engine cut off cleanly. The exhaust plume disappeared. The roar faded to silence.

For a moment, nobody spoke. We just stared at the data, at the beautiful stable lines on the graphs, at the proof that what we'd built actually worked.

Then Maya started laughing. Not hysterical laughter—just the release of four hours of tension. "It worked. It actually worked. You magnificent crazy people, it worked."

Dr. Lal pulled me into a hug that nearly knocked me over. "You did it! Your algorithm—the drift control theory—it translated perfectly! I knew it would, I knew there was something in your approach—"

Gabi was grinning. "That was the cleanest burn we've ever had. Even better than before the instability showed up. The active management system is actually improving performance."

Wrench clapped me on the shoulder hard enough to hurt. "Theory become hardware. Dreams become reality. You starting to understand now?"

Dr. Ramcharan stood quietly, reviewing the data on her tablet. When she finally looked up, she was smiling—genuinely smiling, not the professional expression I'd seen before.

"Good work. All of you." She looked at me specifically. "Especially you. You saw a problem from a completely different angle and solved it in four hours. That's what I recruited you for. That perspective."

The factory team started cheering from somewhere. Word had spread that the test was successful. Even at 2:30 AM, people were celebrating.

"Alright," Dr. Ramcharan said, cutting through the excitement. "We've proven the fix works. But we still need to load trucks in three hours. Wrench, get your team on the engine. Careful disassembly, proper packing, triple-check everything. Gabi, prep the support equipment. Maya, document everything—I want the updated algorithms backed up and verified. Dr. Lal, you and the blogger get some food and coffee. You've earned it."

The team scattered to their assignments. The facility transformed from tense emergency mode to organized chaos of preparation. We had three hours to make the departure window.

We were going to make it.

---

Dr. Lal and I ended up in the cafeteria with Raj and a few other engineers who'd been monitoring the test remotely. Someone had ordered more food—roti from a 24-hour place, chinese from another spot. The early morning meal of people who'd forgotten dinner existed.

"That was insane," Raj said around a mouthful of curry. "You modified core control algorithms in four hours and tested them live. You know how long that normally takes? Months. Months of development and testing and validation."

"We didn't have months," I said simply.

"No, we didn't. But you still did it." He raised his coffee cup in toast. "To the blogger who became a rocket scientist in one week. And saved our asses on day seven."

We drank to that. Bad cafeteria coffee at 3 AM, celebrating a test burn that would never appear in any public record, solving problems that weren't supposed to be possible.

"What made you think of the drift control analogy?" Dr. Lal asked. "I've been working in propulsion for twenty years and never made that connection."

"I spent three years writing about controlling unstable systems," I said. "A car in a drift is constantly on the edge of spinning out. You're not trying to prevent the instability—you're managing it. Seemed like the same principle might apply."

"It's more than that, though." Maya had joined us, laptop in hand. "It's about recognizing patterns across domains. That's rare. Most engineers get so specialized they stop seeing connections. You still see them because you came from outside traditional aerospace."

"The outsider advantage," Raj said. "No preconceptions about how things 'should' be done."

"Also helps that you're not scared," Dr. Lal added. "You proposed a radical solution with four hours to implement it. Most people would have said it's too risky, needs more time, requires extensive testing. You just... did it."

"Calculated risk," I echoed Dr. Ramcharan's earlier words. "Isn't that what we're all doing here?"

"Every day," Maya confirmed. "That's what PROMETHEUS is. The calculated risk that giving humanity the stars is worth the dangers of the fire."

We sat there in the cafeteria, eating roti and chinese food under fluorescent lights while the city slept above us. Through the windows—carefully positioned to show only boring industrial Trinidad—the sky was starting to lighten. Dawn approaching.

Dr. Ramcharan appeared in the doorway. She'd changed from coveralls back to her usual professional attire, somehow looking fresh despite the all-nighter.

"Trucks are loaded," she announced. "Everything's secured. We're ready to roll at 5:30 as planned."

"You're not sleeping?" Dr. Lal asked.

"I'll sleep in Tobago." She poured herself coffee, a rare moment of her actually using the common facilities. "Tonight reminded me why I built this place. Brilliant people, impossible problems, solutions that emerge at 2 AM because someone saw a connection nobody else saw."

She looked at me. "Your first week here, you asked what happens when PROMETHEUS goes public. I told you the world changes. Tonight, you helped ensure we'll get to make that change. The test in Tobago—it needs to work. Needs to be perfect. Because when we announce this, we need to show not just that metallic hydrogen engines are possible, but that they're reliable. Proven. Ready."

"No pressure," I said.

She smiled. "All the pressure. That's what makes it worth doing."

---

By 5 AM, we were all in the hidden garage. Three trucks, loaded with carefully packed equipment, engine components, support systems, and three precious containers of metallic hydrogen. The convoy that would take the future to Tobago.

Colonel Thompson was coordinating security. "Route is planned. No stops except for fuel. Comm check every thirty minutes. If anyone deviates, the whole convoy pulls over until we sort it out. This is valuable cargo—act like it."

Dr. Ramcharan would drive the lead vehicle with Maya. Gabi and Wrench in the second truck with the engine components. Dr. Lal, Raj, and I in the third with support equipment.

"We'll pick up Zay at the Tobago facility," Dr. Ramcharan explained. "He's been prepping the test site all week. By the time we arrive, everything should be ready for integration and final checks."

I looked at my Subaru, sitting alone in the corner of the garage. It would stay here, waiting, while I drove to Tobago in a truck full of rocket parts.

"Your car will be fine," Colonel Thompson said, noticing my glance. "Probably safer here than in your street parking."

"I know. Just strange. Feels like leaving something behind."

"You are," he said simply. "Who you were before. Can't take that to Tobago with you. Only who you're becoming."

The convoy pulled out at 5:32 AM, slightly behind schedule but within acceptable margins. We drove through sleeping Port of Spain, three trucks that looked like any other commercial vehicles, carrying equipment that would change the world if everything went right.

The sun was rising over the Northern Range as we headed south toward the ferry terminal. The city was waking up—early vendors, morning traffic, normal life beginning another normal day.

Nobody looking at us would know. Nobody would guess. Three trucks full of the future, driving past them in the dawn light.

I thought about Marcus and Keisha, probably still sleeping. I'd sent them a text before leaving: *Going out of town for work. Back in a few days. Talk soon.*

Not a lie. Not quite the truth either.

Forward was the only direction left.

Dr. Lal was already dozing in the passenger seat, finally letting exhaustion win. Raj was in the back, headphones on, probably listening to soca and processing the night we'd just had.

I drove, following the lead trucks, watching Trinidad slide past the windows. The island I'd grown up on, the place I thought I knew completely.

Now I knew it held secrets. Underground tunnels and hidden facilities. Impossible materials and engines that shouldn't work. Projects that would give humanity the stars.

And I was part of it. Not just an observer or a blog writer. An actual engineer who'd solved actual problems and helped make actual history.

The tiny machined nozzle from Wrench was in my pocket. I touched it through the fabric, feeling its precision.

Theory become hardware. Dreams become reality.

In a few hours, we'd be in Tobago. In a few days, we'd test a metallic hydrogen engine under real conditions. In a few weeks or months, the world would learn that everything had changed.

But right now, we were just three trucks driving through early morning Trinidad, following the road that led to the ferry, the ocean, and whatever came next.

The road that led to the stars.

Ready or not, here we go.
