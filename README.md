# Регулярные выражения

К сожалению, на практике, мягко говоря, не часто приходится использовать такие шедевры
(к счастью коллег), но дело интересное.

```regexp
@
<(div|li|select)[^>]+(?:some|css|classes)[^>]+>
  (?>
   (?>(?>(?!(?:<\1(?:[^<>]*)>|</\1>)).)+)
     |
   (<\1(?>[^>]*)>(?:(?>(?:(?!(<\1(?>[^>]*)>|</\1>)).)+)|(?-2))*</\1>)   # Xo-Xo-Xo! }:)
  )*
</\1>
@xsi
```

Рекурсивное выражение для поиска HTML тэга в тексте (здесь указаны div, li, select),
например, по классу. С учётом того, что внутри этого тэга может быть неограниченной
вложенности количество таких же тэгов.

div внутри div? Рекурсия найдет нужный.

