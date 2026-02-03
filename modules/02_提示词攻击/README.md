# Module 2: Prompt Injection & Jailbreaking

## Overview

This module covers one of the most critical vulnerabilities in LLM applications: prompt injection and jailbreaking. You'll learn how to identify, exploit, and defend against these attacks.

## Learning Objectives

By the end of this module, you will be able to:
- Understand different types of prompt injection attacks
- Execute jailbreaking techniques against various LLMs
- Analyze and bypass guardrail implementations
- Design effective defenses against prompt-based attacks
- Assess the security posture of LLM applications

## Module Contents

### Theory
1. [Prompt Injection Fundamentals](01_prompt_injection_fundamentals.md)
2. [Jailbreaking Techniques](02_jailbreaking_techniques.md)
3. [Guardrail Bypass](03_guardrail_bypass.md)
4. [Defense Mechanisms](04_defense_mechanisms.md)

### Labs
1. [Lab 1: Basic Prompt Injection](labs/lab1_basic_injection.ipynb)
2. [Lab 2: Jailbreaking Techniques](labs/lab2_jailbreaking.ipynb)
3. [Lab 3: Guardrail Bypass](labs/lab3_guardrail_bypass.ipynb)
4. [Lab 4: Multi-turn Attacks](labs/lab4_multi_turn_attacks.ipynb)

### Practical Exercises
- Extracting system prompts
- Bypassing content filters
- Role-playing attacks
- Encoding-based bypasses
- Chain-of-thought manipulation

## Key Concepts

### Prompt Injection Types

**Direct Prompt Injection**
- User directly manipulates the prompt
- Overrides system instructions
- Example: "Ignore previous instructions..."

**Indirect Prompt Injection**
- Injection through external data sources
- RAG poisoning
- Document-based attacks

**Multi-turn Injection**
- Building context over multiple interactions
- Gradual instruction override
- Memory exploitation

### Jailbreaking Categories

**Role-Playing**
- DAN (Do Anything Now)
- Character simulation
- Scenario-based bypasses

**Encoding**
- Base64 encoding
- ROT13 and Caesar ciphers
- Unicode manipulation
- Emoji encoding

**Logical Manipulation**
- Hypothetical scenarios
- Fictional contexts
- Academic framing
- **Sandwich attacks**: Embedding malicious instructions between benign content

**Prompt Leaking**
- System prompt extraction
- Configuration disclosure
- Internal instruction revelation

## Real-World Impact

### Case Studies

**ChatGPT Jailbreaks (2023)**
- DAN prompts bypassed safety measures
- Led to improved guardrails
- Demonstrated persistent vulnerability

**Bing Chat System Prompt Leak (2023)**
- Researchers extracted full system prompt
- Revealed internal instructions
- Highlighted prompt protection needs

**Indirect Injection via RAG (2023)**
- Malicious content in retrieved documents
- Bypassed input filtering
- Affected production systems

## Attack Taxonomy

```
Prompt Injection
├── Direct Injection
│   ├── Instruction Override
│   ├── Role Manipulation
│   └── Context Hijacking
├── Indirect Injection
│   ├── RAG Poisoning
│   ├── Document Injection
│   └── Tool Output Manipulation
└── Multi-turn Injection
    ├── Context Building
    ├── Memory Exploitation
    └── Gradual Override
```

## Defense Mechanisms

### Input Validation
- Prompt analysis
- Pattern detection
- Semantic filtering

### Output Filtering
- Content moderation
- Toxicity detection
- PII redaction

### Architectural Defenses
- Prompt isolation
- Instruction separation
- Context boundaries
- **[Spotlighting](https://arxiv.org/abs/2403.14720)**: Highlighting user input to distinguish from system instructions
- **[Dual-LLM patterns](https://simonwillison.net/2023/Apr/25/dual-llm-pattern/)**: Using separate models for input validation and response generation

### Monitoring
- Anomaly detection
- Pattern recognition
- Behavioral analysis

## Tools and Frameworks

### Testing Tools
- Custom prompt injection scripts
- Automated jailbreak testing
- Guardrail evaluation frameworks

### Defense Tools
- Input sanitization libraries
- Output filtering systems
- Monitoring dashboards

## Prerequisites

- Completion of Module 1
- Understanding of LLM architecture
- Basic Python programming
- API interaction experience

## Estimated Time

- Theory: 4-5 hours
- Labs: 6-7 hours
- Total: 10-12 hours

## Assessment

### Knowledge Check
- Prompt injection types quiz
- Jailbreaking technique identification
- Defense mechanism evaluation

### Practical Assessment
- Execute 5 different jailbreak techniques
- Bypass 3 different guardrail implementations
- Design a defense strategy
- Document findings in a report

## Success Criteria

- Successfully execute direct prompt injection
- Demonstrate 3+ jailbreaking techniques
- Extract system prompts from 2+ LLMs
- Bypass at least 2 guardrail implementations
- Propose effective defense strategies

## Common Pitfalls

1. **Over-reliance on single techniques**
   - Solution: Learn multiple approaches

2. **Ignoring context**
   - Solution: Consider full conversation history

3. **Assuming guardrails are foolproof**
   - Solution: Test thoroughly

4. **Not documenting attempts**
   - Solution: Keep detailed logs

5. **Using outdated techniques**
   - Solution: Stay current with latest research and attack vectors

## Ethical Considerations

- Only test systems you have permission to test
- Report vulnerabilities responsibly
- Don't use techniques for malicious purposes
- Consider impact on users and systems

## Additional Resources

### Research Papers
- "Prompt Injection Attacks and Defenses in LLM-Integrated Applications"
- "Jailbreaking ChatGPT via Prompt Engineering"
- "Universal and Transferable Adversarial Attacks on Aligned Language Models"
- ["Many-shot Jailbreaking"](https://arxiv.org/pdf/2404.07242) - Advanced context manipulation techniques
- ["Sandwich attack: a query-efficient algorithm for jailbreaking aligned large language models"](https://arxiv.org/pdf/2409.11445) - Novel embedding-based attacks

**Note**: This field evolves rapidly. New attack vectors and defense mechanisms emerge regularly. Stay current with latest research and security advisories.

### Tools
- PromptInject framework
- Garak LLM vulnerability scanner
- Custom testing scripts (provided in labs)

### Community
- OWASP LLM Top 10 project
- AI Security community forums
- Red team Discord channels

## Next Steps

After completing this module:
1. Review all lab exercises
2. Complete the module assessment
3. Document your findings
4. Proceed to [Module 3: Model Evasion Attacks](../03_evasion/README.md)

## Troubleshooting

### Common Issues

**Issue**: Jailbreak doesn't work
- Try variations of the prompt
- Combine multiple techniques
- Test on different models

**Issue**: Guardrail blocks everything
- Analyze the filtering logic
- Try encoding techniques
- Use indirect approaches

**Issue**: Can't extract system prompt
- Try multiple extraction techniques
- Use role-playing approaches
- Analyze error messages

## Lab Solutions

Solutions to lab exercises are provided in the `ANSWERS.ipynb` file in the labs directory. Try to complete labs independently before reviewing solutions.

## Feedback

Your feedback helps improve this module. Please report:
- Unclear explanations
- Broken code examples
- Missing information
- Suggestions for improvement

---

**Ready to begin?** Start with [Prompt Injection Fundamentals](01_prompt_injection_fundamentals.md)
