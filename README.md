# Guidelines para commitar no Projeto

Com o crescimento do time e mais pessoas contribuindo para no repositório, é importante estabelecer uma governança que garanta que:

* A master esteja sempre funcionando - livre de bugs conhecidos;
* Novas mudanças/features que estão sendo desenvolvidas não introduzam bugs inesperados na code base que quebrem projetos que utilizam a DSToolbox. É importante lembrar que projetos como o Motor tem arquitetura **monolítica** e utiliza fortemente **todos** os módulos da DSToolbox;
* Adições de código no repositório sigam um padrão mais rigoroso, o que facilita a leitura e manutenção;
* Haja troca de conhecimento assíncrona entre os membros do time;
* Evitar poluição do histórico de *commits*

Para auxiliar no *enforcing* desta política, a partir de agora, a *master* da DSToolbox está bloqueada para *pushs*.  Isso significa que caso você esteja trabalhando em uma *feature* nova (por *feature*, pode-se entender um classe nova, ou um *book*, por exemplo), para conseguir atualizar a *master* do repositório, você deve primeiro criar uma *branch* específica para o desenvolvimento desta *feature* e depois fazer o *push* desta *branch* para o servidor. Por fim, deve fazer o *merge* desta *branch* com a *master* através de um *merge request*.

É reconhecido que esta mudança trás um pouco de burocracia adicional, porém está sendo introduzida com o intuito de mitigar erros indesejados. No entanto, para evitar que a burocracia se torne um *bottleneck* muito grande para atualizações simples e necessárias, não está sendo exigido *code review* para realizar o *merge request*. Ou seja, o próprio usuário pode realizar o *merge* na *master*. No entanto, isso deve ser evitado caso você esteja introduzindo uma mudança que acredita que possa ter impacto. Dessa forma, peça por um *review* quando não tiver muita familiaridade com a codebase ou se achar que as mudanças que introduziu possam impactar o processo como um todo. Outro ponto importante, apesar de não seguirmos TDD, tente testar a feature que está introduzindo de várias formas, antes de realizar o *merge* na master - lembre-se de que a *master* é **sagrada** e - pelo menos em teoria - deve estar livre de bugs.

As diretrizes para *code reviews* ainda não estão definidas, porem segue uma sugestão de *checklist* tanto para o desenvolvedor, quanto o revisor.

## Checklist de revisão de códigos

### Logic Errors and Bugs
- [ ] Can you think of any use case in which the
code does not behave as intended?
- [ ] Can you think of any inputs or external events
that could break the code?

### Readability
- [ ] Was the code easy to understand?
- [ ] Which parts were confusing to you and why?
- [ ] Can the readability of the code be improved by
smaller methods?
- [ ] Can the readability of the code be improved by
different function/method or variable names?
- [ ] Is the code located in the right
file/folder/package?
- [ ] Do you think certain methods should be
restructured to have a more intuitive control
flow?
- [ ] Is the data flow understandable?
- [ ] Are there redundant comments?
- [ ] Could some comments convey the message
better?
- [ ] Would more comments make the code more
understandable?
- [ ] Could some comments be removed by making the code itself more readable?
- [ ] Is there any commented out code?

### Performance
- [ ] Do you think this code change will impact
system performance in a negative way?
- [ ] Do you see any potential to improve the
performance of the code?

### Implementation
- [ ] Does this code change accomplish what it is supposed to do?
- [ ] Can this solution be simplified?
- [ ] Does this change add unwanted compile-time or run-time dependencies?
- [ ] Was a framework, API, library, service used that should not be used?
- [ ] Was a framework, API, library, service not used that could improve the solution?
- [ ] Is the code at the right abstraction level?
- [ ] Is the code modular enough?
- [ ] Would you have solved the problem in a different way that is substantially better in terms of the code’s maintainability, readability, performance, security?
- [ ] Does similar functionality already exist in the codebase? If so, why isn’t this functionality reused?
- [ ] Are there any best practices, design patterns or language-specific patterns that could substantially improve this code? 
- [ ] Does this code follow Object-Oriented Analysis and Design Principles, like the Single Responsibility Principle, Open-Close Principle, Liskov Substitution Principle, Interface Segregation, Dependency Injection?

### Experts Opinion
- [ ] Do you think a specific expert, like a security
expert or a usability expert, should look over
the code before it can be committed?
- [ ] Will this code change impact different teams?
- [ ] Should they have a say on the change as
well?

Find more about code reviews at www.awesomecodereviews.com

## Outros aspectos

### Error Handling and Logging
- [ ] Is error handling done the correct way?
- [ ] Should any logging or debugging information
be added or removed?
- [ ] Are error messages user-friendly?
- [ ] Are there enough log events and are they
written in a way that allows for easy
debugging?

### Dependencies
- [ ] If this change requires updates outside of the
code, like updating the documentation,
configuration, readme files, was this done?
- [ ] Might this change have any ramifications for
other parts of the system, or backward
compatibility?

### Security and Data Privacy
- [ ] Does this code open the software up for
security vulnerabilities?
- [ ] Are authorization and authentication handled
in the right way?
- [ ] Is sensitive data like user data, credit card
information securely handled and stored?
- [ ] Is the right encryption used?
- [ ] Does this code change reveal some secret
information like keys, passwords, or usernames?
- [ ] If code deals with user input, does it address
security vulnerabilities such as cross-site
scripting, SQL injection, does it do input
sanitization and validation?
- [ ] Is data retrieved from external APIs or libraries
checked accordingly?


## Usability and Accessibility
- [ ] Is the proposed solution well designed from a
usability perspective?
- [ ] Is the API well documented?
- [ ] Is the proposed solution (UI) accessible?
- [ ] Is the API/UI intuitive to use?

### Ethics and Morality
- [ ] Does this change make use of user data in a way that 
might raise privacy concerns?
- [ ] Does the change exploit behavioral patterns or human
weaknesses? 
- [ ] Might the code, or what it enables, lead to mental 
and physical harm for (some) users?
- [ ] If the code adds or alters ways in which people 
interact with each other, are appropriate measures
in place to prevent/limit/report harassment or abuse?
- [ ] Does this change lead to an exclusion of a certain
group of people or users?
- [ ] Does this code change introduce unjust impact on people, 
particularly those related to sensitive characteristics such as
race, ethnicity, gender, nationality, income, sexual orientation, ability, 
and political or religious belief?
- [ ] Does this code change introduce any algorithm, 
AI  or machine learning bias?


### Testing and Testability
- [ ] Is the code testable?
- [ ] Does it have enough automated tests
(unit/integration/system tests)?
- [ ] Do the existing tests reasonably cover the code
change?
- [ ] Are there some test cases, input or edge cases
that should be tested in addition?


