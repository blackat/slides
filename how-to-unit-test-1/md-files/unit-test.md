# Unit Test

- <span class="text-highlight-orange">**Scope.**</span> Single class.
- <span class="text-highlight-orange">**Collaborators.**</span> Substituted with <span class="text-highlight-red">tests doubles.</span> (fake replacements)



# Goal

- <span class="text-highlight-orange">**Idea.**</span> Make sure the class you are working on right now works correctly.
- <span class="text-highlight-orange">**Test.**</span> Verify the <span class="text-highlight-yellow">expected behavior</span> of the class.


# Test in isolation

- <span class="text-highlight-orange">**Forget about everything else.**</span> Focus on the <span class="text-highlight-yellow">single class</span> which must work in any environment (no database, no web service, no other classes).
- <span class="text-highlight-orange">**Test fixture.**</span> <span class="text-highlight-yellow">Well known and fixed environment</span> so that a test result is repeatable.


# Benefits

- <span class="text-highlight-orange">Great accuracy.</span> <span class="text-highlight-red">Documentation</span> of the single class code, more reliable than textual description.
- <span class="text-highlight-orange">Run extremely fast.</span> Immediate feedback on the <span class="text-highlight-yellow">code quality</span>, bugs are immediately blocked.
- <span class="text-highlight-orange">Easy refactor.</span> Refactor your code with no panic, <span class="text-highlight-yellow">the class is covered by unit tests</span>.


# Interactions

<img src="images/interactions.png" alt="Unit test interactions" width="75%"/>

- Direct interaction
- Indirect interaction


# Direct

- <span class="text-highlight-yellow">Between test class and SUT.</span> Directly available in the source code.
- <span class="text-highlight-yellow">Can be controlled.</span> Test class can control the interaction.


# Indirect

- <span class="text-highlight-yellow">Between SUT and DOCs.</span> Cannot be controlled by the test class or client.


# In general

- <span class="text-highlight-yellow">Inputs (direct and indirect).</span> Set the SUT in a required state and invoke its methods.
- <span class="text-highlight-yellow">Outputs (direct and indirect).</span> Used to verify if the SUT is working as expected.


# Not Unit Test If

- Talk to the database
- Communicate across the network
- Touch the file system
- Can't run at the same time as any of other unit tests
- Special configuration to be run
