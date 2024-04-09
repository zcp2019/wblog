n = [];
   n['gdws'] = 1182; //广东卫视
   n['dwqws'] = 1197; //大湾区卫视
   n['dwqws2'] = 1191; //大湾区卫视（海外版）
   n['gdzj'] = 1183; //广东珠江
   n['gdms'] = 1185; //广东民生
   n['gdxw'] = 1186; //广东新闻
   n['gdzy'] = 1198; //广东综艺
   n['gdty'] = 1184; //广东体育
   n['gdys'] = 1199; //广东影视
   n['gdjjkj'] = 1196; //广东经济科教
   n['gdse'] = 1200; //广东少儿
   n['gdyd'] = 2463; //广东移动
   n['jjkt'] = 1187; //嘉佳卡通
   n['gdwh'] = 2511; //GRTN文化
var url = 'https://api.itouchtv.cn:8090/liveservice/v2/tvChannelcontent?sid='+n[vid]+'&channelId=114&fromSource=share&shareTo=WEIXIN&fromSourceParm=0&userPk=0';
var timestamp = (new Date).getTime();
var str = "GET\n"+url+"\n"+timestamp+"\n";
var key = 'HGXimfS2hcAeWbsCW19JQ7PDasYOgg1lY2UWUDVX8nNmwr6aSaFznnPzKrZ84VY1';
var hash = CryptoJS.HmacSHA256(str, key);
var sign = CryptoJS.enc.Base64.stringify(hash);

$.ajax({
  type : 'get',
  url : url,
  dataType : 'json',
  crossDomain: true == !(document.all),
  contentType: 'application/json',
  headers :{
            'X-ITOUCHTV-Ca-Key': '28778826534697375418351580924221',
            'X-ITOUCHTV-Ca-Signature': sign,
            'X-ITOUCHTV-Ca-Timestamp': timestamp,
            'X-ITOUCHTV-CLIENT': 'ews_APP',
            'x-itouchtv-device-id': 'IMEI_867464032598278',
            'x-itouchtv-ts': timestamp
           },
   success: function(data) {
      m3u8 = data.tvChannel.videoUrl;
      location.href = 'vlc.htm?id=' + m3u8;
   }
})