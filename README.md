# home-assistant snippets


## Count lights with state
Count lights with state on. light.wohnzimmer_licht combine multiple lights into one entity. Its entity type is light.group. (https://www.home-assistant.io/integrations/light.group/)

```
{% set count = namespace(value=0) %}
{% if state_attr('light.wohnzimmer_licht', 'entity_id') != None -%}
  {% for id in state_attr('light.wohnzimmer_licht', 'entity_id') -%}
    {% if is_state(id, "on") -%}
      {% set count.value = count.value + 1 %}
    {%- endif %}
  {%- endfor %}
{%- endif %}
{{ count.value }
```
