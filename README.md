# Alias
        touch    = "!f() { touch $1; git add $1; }; f"
        commita  = "!f() { git commit -am \"$1\"; }; f"
        unadd    = "!f() { git rm --cached $1; }; f"
        pushu    = "!f() { git push -u origin HEAD; }; f"
        deploy   = "!f() { git commita \"$1\"; git pushu; if [ \"$2\" = \"-pr\" ]; then gh pr create --title \"$1\" --body \"\"; fi }; f"
        ignore   = "!f() { git update-index --skip-worktree $1; }; f"
        unignore = "!f() { git update-index --no-skip-worktree $1; }; f"
        resolve  = "!f() { git restore $1 $2; git add $1; GIT_EDITOR=/bin/true git merge --continue; }; f"
        
        
# Hooks
## pre-commit => npm t
## commit-prepare-msg => echo "\n\nCo-authored-by: name <name@example.com>" >> $1
