# Mustachuate

Mustachvulate is a fork of a fork of Mustache which uses govaluate in order to allow for more flexibility with variables.

### Example

```
Welcome {{member.User.Username}} to {{guild.Name}}! You are the {{Ordinal(guild.MemberCount)}} user.
{{#invite}}Invited by {{invite.CreatedBy.Name}}{{/invite}}{{^invite}}No invite was found :({{/invite}}
Roles:
{{#member.Roles}}{{Name}}\n{{/member.Roles}}
```

becomes

```
Welcome ImRock to Welcomer Support Guild! You are the 200th user.
No invite was found :(
Roles:
Owner
Members
@everyone
```

Using Mastachuate:
```
  res, err := a.Render(map[string]govaluate.ExpressionFunction{
  	"Ordinal": func(args ...interface{}) (interface{}, error) {
    	number := args[0].(float64)
        return humanize.Ordinal(int(number)), nil
    },
	}, map[string]interface{}{
    	...data goes here
  	}
  )
```
All the builtin Renders that mustache use will fully work.

Todo:
- [ ] Ability to filter how strict govaluate errors are (not panicking on issues)
- [ ] Ability to list exactly what expressions are causing errors.

#### Credits
- [Govaluate](https://github.com/Knetic/govaluate)
- [Mustache](https://github.com/cbroglie/mustache)

#### Note
Whilst passing most, it seems to fail some tests however these are either insentric to the origional fork or are not replicatable issues and may just be issues with some of the testing.