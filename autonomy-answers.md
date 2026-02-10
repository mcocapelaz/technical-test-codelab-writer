# Autonomy Scenarios 

## Scenario 1: Undocumented API Behavior

### How would you determine the API's behavior for invalid inputs?

As someone transitioning from communication to technical writing, I would combine my research skills with hands-on testing. 

1. **Start with practical testing:**
   - Use Postman (a tool I've learned for API testing) to send different types of invalid data
   - Document what happens with each test: What error message appears? What status code?
   - Test obvious cases first: empty fields, wrong data types, missing required information
   - Keep detailed notes in a spreadsheet tracking input → output for each test

2. **Learn from existing patterns:**
   - Look at how other similar endpoints in the API handle errors
   - Check if there's existing documentation for other POST endpoints that might follow the same pattern
   - Review any example code or tutorials that use this API

3. **Leverage available resources:**
   - Search internal Slack/Teams channels for discussions about this API
   - Check if there are recorded demos or presentations about the API
   - Look for code examples in the company's GitHub repositories
  
4. **Ask for help strategically:**
   - Reach out to developers who have used this API (even if the main team is away)
   - Post questions in internal developer channels with specific examples
   - Consult with senior technical writers about similar experiences

### What would you include in your codelab to help developers handle edge cases?

1. **Clear, user-friendly error documentation:**
   - A simple table showing "What you send" vs. "What happens" with plain-language explanations
   - Real error message examples with translations of what they mean in practice
   - Visual formatting (callout boxes, icons) to make errors easy to scan

2. **Practical troubleshooting section:**
   - "Common mistakes" section based on my testing
   - Step-by-step debugging guidance: "If you see this error, check..."
   - Links to related documentation or support channels

3. **Transparent communication:**
   - Honest note: "This behavior was tested and documented through hands-on experimentation. Please verify with the API team if you encounter unexpected results."
   - Date stamp and version information for future reference
   - Clear call-to-action: "Found different behavior? Report it here: [link]"

4. **Code examples with comments:**
   - Working example showing proper error handling
   - Inline comments explaining why each validation check matters
   - Links to additional resources for developers who want deeper technical details

**My communication background helps me** focus on clarity and user experience rather than just technical accuracy.

### How would you document your findings for future reference?

1. **Create a clear internal document:**
   - Write a summary report of my testing process and findings
   - Include the Postman collection I used (so others can reproduce my tests)
   - Use screenshots and annotations to make it visual and accessible
   - Store it in the team's documentation repository with clear naming

2. **Share appropriately:**
   - Share in the team channel with a brief summary
   - Link it from the published codelab for future writers

3. **File an official documentation request:**
   - Open a documentation alignment request to share findings regarding the current API behavior.
   - Attach my findings as supporting material
   - Use my communication skills to write a clear, actionable request
   - Offer to collaborate on improving the official docs

4. **Update team processes:**
   - Suggest adding "API behavior testing protocol" to our workflow
   - Share lessons learned in a team meeting
   - Contribute to documentation best practices guide

---

## Scenario 2: Conflicting Information

### How would you determine which method is the correct/recommended one?

1. **Assess source authority and recency:**
   - Check when the official Spring Boot documentation was last updated
   - Look at the template's git history to see when it was created
   - Compare dates to see which information is most current

2. **Research the context:**
   - Use Google and Stack Overflow to understand the broader community perspective
   - Search for "Spring Boot best practices 2026"
   - Check Spring Boot release notes for deprecation warnings
   - Look for blog posts from Spring team members or recognized experts

3. **Consult with subject matter experts:**
   - Schedule a quick call with a senior developer on my team
   - Ask in the internal Spring Boot channel: "I found three different authentication methods, which should I use and why?"
   - Frame questions clearly: "For a codelab targeting Spring Boot 3.x, I see method A, B, and C. What's the current best practice?"

4. **Test all three approaches myself:**
   - Even though I'm junior in programming, I can follow tutorials and compare:
     - Which one is easier to explain in a codelab?
     - Which produces clearer error messages?
     - Which requires fewer dependencies or setup steps?

### What criteria would you use to make your decision?

1. **Source credibility:**
   - Official documentation > Internal expert > Template precedent
   - Recent information > older information
   - Verified by multiple sources > single source

2. **Pedagogical clarity:**
   - Which method is easiest to teach in a step-by-step format?
   - Which will cause fewer problems for learners?
   - Which has the clearest error messages if something goes wrong?

3. **Practical considerations:**
   - Alignment with company standards (I'd check with my team)
   - Fewer external dependencies = simpler for users
   - Better error handling = better user experience

4. **Future-proofing:**
   - Is this approach likely to change in the next major version?
   - Does it follow current industry trends?
   - Is there good community support if users have issues?

5. **Risk management:**
   - Security implications (I'd explicitly ask a security-focused developer about this)
   - Maintenance burden (will this method become outdated quickly?)

### How would you proceed if you couldn't get a definitive answer before your deadline?

1. **Make a defensible choice:**
   - Choose the official documentation method (method A) as it's the safest default
   - Document why I chose it in my working notes

2. **Be transparent in the codelab:**
   - Add a clear callout box: "Note: There are multiple ways to configure Spring Boot authentication. This codelab uses [method A] following the official Spring Boot documentation as of [date]."
   - Include a "Further Reading" section mentioning the other approaches with brief context

3. **Create clear, modular content:**
   - Write sections so they could be easily updated later
   - Use descriptive section headers that make it easy to find and modify specific parts
   - Add internal comments in code samples noting decision points

4. **Document the uncertainty:**
   - Create an internal note for the team: "Codelab published with method A due to conflicting info. Needs review when [expert] is available."
   - Set a calendar reminder to revisit after publication
   - Add to the codelab's metadata: "Review needed: authentication method"

5. **Communicate proactively:**
   - In my publication notes, explain: "Three valid methods found. Published with official docs method. Open to updating if team has different preference."
   - Show my research process so reviewers understand my reasoning
   - Frame it as a learning opportunity: "Would appreciate technical review on this choice"

---

## Scenario 3: Last-Minute Breaking Changes

### What's your immediate action plan?

**First 15-30 minutes - Assess and communicate:**

1. **Get clarity on the technical issue:**
   - Ask the developer: "Can you send me the changelog or a list of what specifically breaks?"
   - Ask: "Are there migration docs or examples of code updated to 5.20.0?"
   - Request: "Can you point me to the exact breaking changes that affect authentication and configuration?"

2. **Honest stakeholder communication:**
   - Immediately message the publication coordinator: "Issue discovered - the framework version has a critical bug. Getting details now. Will update you in 30 minutes with a plan."
   - Be transparent: I need to understand the technical changes before estimating fix time

3. **Quick self-assessment:**
   - Can I make these changes myself, or do I need developer help?
   - How much do I understand about what needs to change?
   - What's the realistic timeline given my junior technical level?

4. **Get technical support lined up:**
   - Reach out to the developer who flagged this: "Can you be available for questions as I update this?"
   - Alert my technical writing mentor or a senior dev on my team
   - Better to ask for help early than miss the deadline or publish broken content

### How would you efficiently identify all the changes needed in your codelab?

1. **Create a systematic checklist:**
   ```
   ☐ Update version number references 
   ☐ Review Step 3: Authentication (developer said this breaks)
   ☐ Review Step 7: Configuration (developer said this breaks)
   ☐ Check all code snippets for affected methods
   ☐ Update screenshots that show version numbers
   ☐ Update GitHub repository links/branches
   ☐ Check introduction and prerequisites sections
   ```

2. **Use search effectively:**
   - Search document for "5.18" to find all version references
   - If the developer mentioned specific method names, search for those
   - Look for related terms (if "configureAuth()" changed, search for "auth")

3. **Leverage the developer's expertise:**
   - Ask: "Can you review my codelab and flag exactly where the breaking changes apply?"
   - Request: "Could you provide the before/after code for these two sections?"
   - This acknowledges my technical limitations while ensuring accuracy

4. **Use diff tools strategically:**
   - If I have working code in a repo, ask the developer to update it and show me the diff
   - Use GitHub's compare feature to see exact changes
   - This helps me understand what changed even if I don't know why

5. **Structured comparison:**
   - Open the framework documentation for both versions side-by-side
   - Create a simple table: "Step | Old Way (5.18) | New Way (5.20) | Why It Changed"
   - This helps me understand and also serves as review documentation

**Honestly, I'd lean heavily on technical help here** - my communication skills let me ask clear questions and document changes, but I need support on the technical specifics.

### How would you verify that your updated codelab works correctly with limited time?

1. **Be honest about testing limitations:**
   - I know how to follow steps and verify outcomes, but I might not catch subtle technical issues
   - I'd explicitly request technical review: "I've updated the codelab, but I need a developer to validate the technical accuracy."

2. **Do what I can test:**
   - Follow the codelab steps exactly as a user would
   - Verify each command runs without errors
   - Check that the final application starts and responds
   - Take screenshots proving it works

3. **Leverage help efficiently:**
   - Ask the developer who reported the issue: "Can you do a quick smoke test of the updated steps?"
   - Request: "Please run steps 3 and 7 specifically and confirm they work"
   - This takes them 10 minutes but gives me confidence

4. **Use automated testing if available:**
   - If the code repository has tests, run them
   - Even if I don't fully understand the tests, I can verify they pass
   - Document: "All automated tests pass with version 5.20.0"

5. **Document testing scope:**
   - Be transparent: "Tested on macOS following all codelab steps. Technical review by [developer name]."
   - This shows what was verified without claiming more expertise than I have

### What would you communicate to stakeholders, and when?

**Immediate notification (15 minutes after learning about issue):**

**To:** Publication coordinator, manager
**Message:**
> "Critical update needed: Version 5.18.0 has a bug, must update to 5.20.0 which has breaking changes in Steps 3 and 7. I'm working with [developer name] to understand the technical changes. Will have an action plan within 45 minutes.
> 
> Heads up: I may need a few hours delay to ensure technical accuracy and get proper review."

---

**Update 1 (45-60 minutes later):**

**To:** Publication coordinator, manager, supporting developer
**Message:**
> "Update plan:
> - Identified 2 steps needing technical updates (Steps 3, 7)
> - [Developer] is providing updated code examples
> - I'll update documentation, screenshots, and explanatory text
> - Will need [developer] to review technical accuracy before publication
> 
> Realistic timeline: 4 hours total (2 hours updates + 1 hour review + 1 hour buffer)
> 
> Recommendation: Delay publication by 6 hours to [new time]. This ensures quality and accuracy.
> 
> I'm being transparent: As a junior developer, I want to ensure technical correctness with expert review rather than rush."

---

**Update 2 (when ready for review):**

**To:** Supporting developer + stakeholders
**Message:**
> "Updates complete and ready for technical review:
> 
> Changes made:
> - Updated all version references to 5.20.0
> - Rewrote Step 3 authentication setup based on provided example
> - Updated Step 7 configuration with new property names
> - Replaced 3 screenshots
> - Updated code repository to version 5.20.0
> 
> What I need:
> - [Developer]: Please review Steps 3 and 7 for technical accuracy
> - Confirm the authentication code works as expected
> - Verify I haven't introduced any technical errors
> 
> Once approved, ready for immediate publication."

---

**Final message (after review and publication):**

**To:** All stakeholders
**Message:**
> "✅ Codelab published successfully with version 5.20.0
> 
> Final updates:
> - Technical review completed by [developer]
> - All steps tested and verified working
> - Code repository updated: [link]
> 
> Thanks to [developer] for the quick turnaround on reviewing technical changes.
> 
> I'll monitor user feedback closely for the next 48 hours. Please alert me to any issues reported."

---

**Post-publication (1-2 days later):**

**To:** Team
**Message:**
> "Post-launch update:
> - No critical issues reported
> - Received positive feedback on clarity of updated steps
> 
> Lessons learned:
> - Having a technical reviewer on standby is crucial for emergency updates
> - Need earlier visibility into framework release schedules
> 
> Suggestion: Can we set up alerts for major version changes in frameworks we document?"

---

**My communication approach:**
- **Honest about limitations:** I'm junior technically, so I involve experts
- **Clear expectations:** Tell people what I can vs. can't do independently
- **Proactive collaboration:** Ask for help early, not when it's too late
- **Transparent process:** Show my work so others can verify
- **Professional tone:** Calm and solution-focused even under pressure
- **Continuous improvement:** Suggest process improvements based on experience

---

## Conclusion

My responses reflect my actual background:

**Strengths I bring:**
- Strong communication and stakeholder management skills
- Excellent at researching, synthesizing information from multiple sources
- User-focused approach to documentation (clarity over technical showmanship)
- Honest about knowledge gaps and proactive about getting help
- Systematic, process-oriented thinking from my communication experience

**My approach:**
- Ask clear, specific questions to get the technical help I need
- Build relationships with developers who can review my work
- Focus on what I can test and verify myself
- Be transparent about limitations while demonstrating problem-solving
- Leverage my communication expertise to document, organize, and explain

I understand that technical writing isn't about being the best programmer—it's about clearly communicating technical concepts, collaborating with experts, and serving user needs. My communication background is an asset, and I supplement my growing technical skills with strategic collaboration.

