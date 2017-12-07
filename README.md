$overflow: hidden;
$box-sizing: border-box;
$padding:15px;


.container,.container-fluid{
  height: auto;
  overflow: $overflow;
  box-sizing: $box-sizing;
  margin: 0 auto;
  padding-left: $padding;
  padding-right: $padding;
}
.row{
  width: 100%;
  height: auto;
  overflow:$overflow ;
  padding-left: -$padding;
  padding-right:- $padding;
  box-sizing: $box-sizing;

}
.row:after,.row:before{
  content: "";
  display: block;
  width: 0;
  height: 0;
  line-height: 0;
  clear: both;
}

[class*="col-"]{
  float: left;
  box-sizing: $box-sizing;
}

//混合宏
@mixin xun($type,$count){
  @for $a from 1 through 12{
    .col-#{$type}-#{$a}{
      width:1/$count*100%*$a;
      padding:$padding;
    }
  }
}
//pc大屏 col-lg
@media screen and (min-width: 1200px) {
  .container{
    width: 1170px;
  }
  @include xun(lg,12);

}
//pc小屏 col-md
@media screen and (max-width: 1200px) and (min-width: 992px) {
  .container{
    width: 970px;
  }
  @include xun(md,12);

}
/* 平板端 col-sm*/
@media screen and (max-width: 992px) and (min-width: 768px) {
  .container{
    width: 750px;
  }
  @include xun(ms,12);
}
//手机屏 col-xs
@media screen and (max-width: 1200px) {
  @include xun(xs,12);

}
