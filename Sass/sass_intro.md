```
@mixin textColor($color){
	color: $color;
}

.box {
	@include textColor(blue);
}


$name: foo;
$attr: border;
 
p.#{$name} {
  #{$attr}-color: blue;
}


$type: monster;
p {
  @if $type == ocean {
    color: blue;
  } @else if $type == matador {
    color: red;
  } @else if $type == monster {
    color: green;
  } @else {
    color: black;
  }
}

```
