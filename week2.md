working1
working2
new line

 branch merged into main
* main
  week2b
 branch not merged into main
  wip

### What happened during rebase?
When rebasing the 'experiment' branch onto 'main', Git temporarily removed the new commits made on 'experiment' (exp1 and exp2). It then updated the base of the 'experiment' branch to point to the latest commit of 'main'. Finally, it reapplied those removed commits on top of the new base. This process rewrites the commit history into a clean, linear line instead of a diverged graph.
