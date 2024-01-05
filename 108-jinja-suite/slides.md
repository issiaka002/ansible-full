%title: ANSIBLE
%author: xavki
%Vidéos: [Formation Ansible](https://www.youtube.com/playlist?list=PLn6POgpklwWoCpLKOSw3mXCqbRocnhrh-)
%blog: [Xavki Blog](https://xavki.blog)


# ANSIBLE : FILTRE 2 - Files & Types ansible


<br>

* capitalize : majuscule premier caractère


```
  - name: debug
    debug:
      msg: |
        {{ var1 | capitalize }}
```

<br>

* file/directory...

```
{{ path is file }}
{{ path is directory }}
{{ path is exists }}
{{ path is abs }}
{{ path is mount }}
{{ path is link }}
```

---------------------------------------------------------------------------------

# ANSIBLE : FILTRE 1 - Files & Types ansible


<br>

* opérateur ansible

```
{{ __result is success }}
{{ __result is changed }}
{{ __result is changed }}
{{ __result is failed }}
{{ ansible_facts['distribution_version'] is version('10', '>=') }}
{{ variable is vault_encrypted }}
```

---------------------------------------------------------------------------------

# ANSIBLE : FILTRE 1 - Files & Types ansible

<br>

* join : concatener une liste

```
{{ var1 | join(" ") | capitalize }}
```

<br>

* split 

```
{{ "192.168.0.17".split(".") }}
{{ "192.168.0.17".split(".") | join("/") }}
```

---------------------------------------------------------------------------------

# ANSIBLE : FILTRE 1 - Files & Types ansible

<br>

* bit vs bytes (1B = 8b)

```
{{ 102400000|human_readable(unit="G") }}
{{ 102400000|human_readable(isbits=True, unit="G") }}
```

* et l'inverse

```
{{'10.00 KB'|human_to_bytes}}
{{'10.00 Kb'|human_to_bytes(isbits=True)}}
```

---------------------------------------------------------------------------------

# ANSIBLE : FILTRE 1 - Files & Types ansible

<br>

* débug de type

```
typeDeVar1: "{{ configuration2 | type_debug }}"
```

<br>

* combine : concaténation de dictionnaires

```
  vars:
    var1: 
      - a: 1
      - b: 2
      - c: 3
    var2: 
      - A: 3
      - B: 4
      - C: 5
    var3: 
      - A: 6
      - E: 4
      - F: 5
  tasks:
  - name: test
    copy:
      content: |
        {{ var1 | combine(var2,var3) }}
      dest: /tmp/xavki.txt
```

---------------------------------------------------------------------------------

# ANSIBLE : FILTRE 1 - Files & Types ansible

<br>

* récupérer des éléments d'une liste pur en refaire une autre

```
{{ [0,2] | map('extract', ['x','y','z']) | list }}
```

```
{{ ['x','y'] | map('extract', {'x': 42, 'y': 31, 'z': 53}) | list }}
```

<br>

* créer une liste de liste

```
{{ [1,2,3,4,5] | zip(['a','b','c','d','e','f']) | list }}
```

