## Description
A switch allows a condition to be tested against a list of (cases) values.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| uniqueresult | unique, first | Whether to stop execution of other skills if a condition was met | true |
| condition |           | A condition to test for                                              |         |
| cases     |           | A list of cases to evaluate                                          |         |


## Examples
```yml
MyCoolMob:
  Type: ZOMBIE
  Skills:
    - switch{condition=entitytype{t=<case>};cases=
        case SKELETON=[
          - message{m="A SKELETON JUST HIT ME"} @Server
          ]
        case HUSK=[
          - message{m="A HUSK JUST HIT ME!"} @Server
          ]
        case PIG=[
          - message{m="NOOO A PIG"} @Server
          ]
        case DEFAULT=[
          - message{m="SOMEONE or SOMETHING HIT ME OUT OF NOWHEREE!!"} @Server
          ]
      } @trigger ~onDamaged
```


<!--TAGS-->
<!--tag:Meta-->
<!--tag:Meta-Mechanic-->

