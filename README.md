# -if($text != "/start"){
$x = file_get_contents("https://github.com/search?q=".urlencode($text)."&type=");
preg_match_all('#<a class="Link--muted" href="(.*)">#',$x,$a);
for($i=0;$i<10;$i++){
$v = str_replace("stargazers","",$a[1][$i]);
$keyboard["inline_keyboard"][] = [['text'=>"$v",'callback_data'=>$v]];
}
$reply_markup = json_encode($keyboard);
bot('sendmessage',[
'chat_id'=>$chat_id,
'text'=>"• نتائج بحث كيثاب ل ~(#$text)
اضغط للتحميل 👇
",
"reply_markup"=>$reply_markup
]);
}
if(preg_match('#/(.*?)/#',$data)){
$repla = "https://github.com".$data."/archive/master.zip";
$repla2 = "https://github.com".$data."/archive/main.zip";
bot('senddocument',['chat_id'=>$chat_id2,
'document'=>$repla2]);
bot('senddocument',['chat_id'=>$chat_id2,
'document'=>$repla
]);}

حماية جروبات 
