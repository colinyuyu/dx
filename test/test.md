数据流向：
从syflixOTT后台里添加点播数据，会自动同步到8K 的后台里。
接口：http://syflixapp.iptv10k.com/import/vod/
方式：Post
参数： 
  1）timestamp : 时间戳（秒）
  2）key : md5("3jIOcUbyl9VQ4BAV" + timestamp) 32位大写
  3）data: ImportVod结构体数组的json字符串格式。下面是例子和对应结构体（golang语言的）  
data数据的例子如下：
[{"InputDefLangId":0,"CategoryMainId":112,"SourceType":"vod888","MovieLang":[{"MovieName":"天龙八部","MovieSummary":"北宋年间，丐帮乔峰被指为契丹人后裔，受尽中原武林人士唾弃。乔峰四处求证，期间与大理世子段誉及少林寺虚竹和尚结拜为兄弟。乔峰屡遭奸人陷害，错杀红颜知己阿朱，为救阿朱妹妹阿紫寻医至大辽，在成为辽南院大王后终与中原武林决裂。辽发兵攻宋朝，萧峰不愿生灵涂炭，以死相搏，最终促辽宋言和。段誉为人豁达开朗，逃避习武却屡获奇功；先后留情于木婉清、钟灵，却痴恋貌若天仙的王语嫣，但王语嫣只钟情其表哥慕容复，三人陷入一段纠缠不清的苦恋。虚竹天性纯良，深得高人指点，武功高强，宅心仁厚的他因缘契合，成就了与梦姑的一段奇缘，成为西夏驸马。在宋辽相争的时势下，各种江湖及情感上的恩恩怨怨正等着他们去面对，几人的不同际遇、情感上的纠葛共同构成了大义情操、壮士英雄的豪情壮志","LangId":1},{"MovieName":"天龍八部","MovieSummary":"北宋年間，丐幫喬峰被指為契丹人後裔，受盡中原武林人士唾棄。喬峰四處求證，期間與大理世子段譽及少林寺虛竹和尚結拜為兄弟。喬峰屢遭奸人陷害，錯殺紅顏知己阿朱，為救阿朱妹妹阿紫尋醫至大遼，在成為遼南院大王後終與中原武林決裂。遼發兵攻宋朝，蕭峰不願生靈塗炭，以死相搏，最終促遼宋言和。段譽為人豁達開朗，逃避習武卻屢獲奇功；先後留情於木婉清、鐘靈，卻癡戀貌若天仙的王語嫣，但王語嫣只鐘情其表哥慕容復，三人陷入一段糾纏不清的苦戀。虛竹天性純良，深得高人指點，武功高強，宅心仁厚的他因緣契合，成就了與夢姑的一段奇緣，成為西夏駙馬。在宋遼相爭的時勢下，各種江湖及情感上的恩恩怨怨正等著他們去面對，幾人的不同際遇、情感上的糾葛共同構成了大義情操、壯士英雄的豪情壯誌","LangId":2},{"MovieName":"Tianlong Eighth Division","MovieSummary":"During the Northern Song Dynasty, Qiao Feng of the Beggars' Sect was referred to as a descendant of the Khitan people, and was rejected by the Wulin people in the Central Plains. Qiao Feng asked for evidence everywhere, and became sworn brothers with Duan Yu, the son of Dali, and the Xuzhu Monk of Shaolin Temple. Qiao Feng was repeatedly framed by villains and killed her confidant Ah Zhu by mistake. In order to save Ah Zhu's sister, Ah Zi, he went to Da Liao to seek medical treatment. After becoming the king of the Liaonan Courtyard, he finally broke with the Central Plains Wulin. Liao sent troops to attack the Song Dynasty, but Xiao Feng didn't want to lose his life. He fought with death to finally promote the peace between Liao and Song. Duan Yu is open-minded and open-minded. He escapes from martial arts practice but has repeatedly achieved marvelous feats; He has been merciful to Mu Wanqing and Zhong Ling, but he is infatuated with Wang Yuyan, who looks like an immortal","LangId":3}],"SourceId":2,"AdminId":0,"MovieName":"天龙八部","MovieSummary":"北宋年间，丐帮乔峰被指为契丹人后裔，受尽中原武林人士唾弃。乔峰四处求证，期间与大理世子段誉及少林寺虚竹和尚结拜为兄弟。乔峰屡遭奸人陷害，错杀红颜知己阿朱，为救阿朱妹妹阿紫寻医至大辽，在成为辽南院大王后终与中原武林决裂。辽发兵攻宋朝，萧峰不愿生灵涂炭，以死相搏，最终促辽宋言和。段誉为人豁达开朗，逃避习武却屡获奇功；先后留情于木婉清、钟灵，却痴恋貌若天仙的王语嫣，但王语嫣只钟情其表哥慕容复，三人陷入一段纠缠不清的苦恋。虚竹天性纯良，深得高人指点，武功高强，宅心仁厚的他因缘契合，成就了与梦姑的一段奇缘，成为西夏驸马。在宋辽相争的时势下，各种江湖及情感上的恩恩怨怨正等着他们去面对，几人的不同际遇、情感上的纠葛共同构成了大义情操、壮士英雄的豪情壮志","PartCount":48,"ImageUrl":"https://bkimg.cdn.bcebos.com/pic/34fae6cd7b899e510fb3213fdcefce33c895d143a7ca","Director":"于荣光","Actor":"杨祐宁,白澍,张天阳,苏青","Lang":"汉语普通话","LangLang":[{"Name":"汉语普通话","LangId":1},{"Name":"漢語普通話","LangId":2},{"Name":"chinese","LangId":3}],"Area":"中国大陆","AreaLang":[{"Name":"中国大陆","LangId":1},{"Name":"中國大陸","LangId":2},{"Name":"Chinese Mainland","LangId":3}],"Label":"武侠剧","LabelLang":[{"Name":"武侠剧","LangId":1},{"Name":"武俠劇","LangId":2},{"Name":"Wu Xia Ju","LangId":3}],"CategroyName":"武侠","CategoryLang":[{"Name":"武侠","LangId":1},{"Name":"武俠","LangId":2},{"Name":"Wu Xia","LangId":3}],"KeywordFirstLetter":"tlbb tianlongbabu Tianlong Eighth Division","PlayDate":"2018","IsShow":1,"UpdateTimeInfo":"","SetsSort":0,"PlayList":[{"PlayLang":[{"Name":"第1集","LangId":1},{"Name":"劇集1","LangId":2},{"Name":"Eposide 1","LangId":3}],"Name":"eposide 1","SeasonNum":0,"FileSortId":1,"IsShow":1,"PlayUrl":[{"FileUrl":"http://www.baidu.com/1.flv","FileType":2,"VideoQuality":"SD","LineId":0}],"SrtList":null},{"PlayLang":[{"Name":"第2集","LangId":1},{"Name":"劇集2","LangId":2},{"Name":"Eposide 2","LangId":3}],"Name":"eposide 2","SeasonNum":0,"FileSortId":2,"IsShow":1,"PlayUrl":[{"FileUrl":"http://www.baidu.com/2.flv","FileType":2,"VideoQuality":"SD","LineId":0}],"SrtList":null},{"PlayLang":[{"Name":"第3集","LangId":1},{"Name":"劇集3","LangId":2},{"Name":"Eposide 3","LangId":3}],"Name":"eposide 3","SeasonNum":0,"FileSortId":3,"IsShow":1,"PlayUrl":[{"FileUrl":"http://www.baidu.com/3.flv","FileType":2,"VideoQuality":"SD","LineId":0}],"SrtList":null},{"PlayLang":[{"Name":"第4集","LangId":1},{"Name":"劇集4","LangId":2},{"Name":"Eposide 4","LangId":3}],"Name":"eposide 4","SeasonNum":0,"FileSortId":4,"IsShow":1,"PlayUrl":[{"FileUrl":"http://www.baidu.com/4.flv","FileType":2,"VideoQuality":"SD","LineId":0}],"SrtList":null},{"PlayLang":[{"Name":"第5集","LangId":1},{"Name":"劇集5","LangId":2},{"Name":"Eposide 5","LangId":3}],"Name":"eposide 5","SeasonNum":0,"FileSortId":5,"IsShow":1,"PlayUrl":[{"FileUrl":"http://www.baidu.com/5.flv","FileType":2,"VideoQuality":"SD","LineId":0}],"SrtList":null},{"PlayLang":[{"Name":"第6集","LangId":1},{"Name":"劇集6","LangId":2},{"Name":"Eposide 6","LangId":3}],"Name":"eposide 6","SeasonNum":0,"FileSortId":6,"IsShow":1,"PlayUrl":[{"FileUrl":"http://www.baidu.com/6.flv","FileType":2,"VideoQuality":"SD","LineId":0}],"SrtList":null},{"PlayLang":[{"Name":"第7集","LangId":1},{"Name":"劇集7","LangId":2},{"Name":"Eposide 7","LangId":3}],"Name":"eposide 7","SeasonNum":0,"FileSortId":7,"IsShow":1,"PlayUrl":[{"FileUrl":"http://www.baidu.com/7.flv","FileType":2,"VideoQuality":"SD","LineId":0}],"SrtList":null},{"PlayLang":[{"Name":"第8集","LangId":1},{"Name":"劇集8","LangId":2},{"Name":"Eposide 8","LangId":3}],"Name":"eposide 8","SeasonNum":0,"FileSortId":8,"IsShow":1,"PlayUrl":[{"FileUrl":"http://www.baidu.com/8.flv","FileType":2,"VideoQuality":"SD","LineId":0}],"SrtList":null},{"PlayLang":[{"Name":"第9集","LangId":1},{"Name":"劇集9","LangId":2},{"Name":"Eposide 9","LangId":3}],"Name":"eposide 9","SeasonNum":0,"FileSortId":9,"IsShow":1,"PlayUrl":[{"FileUrl":"http://www.baidu.com/9.flv","FileType":2,"VideoQuality":"SD","LineId":0}],"SrtList":null}]}]

下面是对应的相关结构体，data数据的最外层是：ImportVod数组，就不展示了。

type ImportVod struct {
	InputDefLangId     int    `json:"InputDefLangId"` //忽略
	CategoryMainId     int    `json:"CategoryMainId"` //主分类ID, 固定值：112
	SourceType         string `json:"SourceType"`     //某某来源，这个以后不能变更了，本次固定值：vod888
	MovieLang          []MovieLangStruct
	SourceId           int          `json:"SourceId"` //唯一标识源的ID，这样添加不会重复
	AdminId            int          `json:"AdminId"`  //固定值0
	MovieName          string       `json:"MovieName"`
	MovieSummary       string       `json:"MovieSummary"`
	PartCount          int          `json:"PartCount"` //集数  part_count
	ImageUrl           string       `json:"ImageUrl"`  //图片封面  image_url
	Director           string       `json:"Director"`  //导演或电台  director
	Actor              string       `json:"Actor"`     //主演  actor
	Lang               string       `json:"Lang"`      //语言  use_language
	LangLang           []LangStruct `json:"LangLang"`
	Area               string       `json:"Area"` //地区  use_language
	AreaLang           []LangStruct `json:"AreaLang"`
	Label              string       `json:"Label"`
	LabelLang          []LangStruct `json:"LabelLang"`
	CategroyName       string       `json:"CategroyName"`
	CategoryLang       []LangStruct `json:"CategoryLang"`
	KeywordFirstLetter string       `json:"KeywordFirstLetter"` //名称首字母拼接  keyword_first_letter
	PlayDate           string       `json:"PlayDate"`           //上映时间  play_date
	IsShow             int          `json:"IsShow"`             //是否显示:0=隐藏,1=显示 控制上下架  is_show
	UpdateTimeInfo     string       `json:"UpdateTimeInfo"`     //更新时间  update_time_info
	SetsSort           int          `json:"SetsSort"`           //排序:0=正序,1=倒序   sets_sort
	PlayList           []Episodes   `json:"PlayList"`
}
type Episodes struct {
	PlayLang   []LangStruct `json:"PlayLang"`
	Name       string       `json:"Name"`       //默认片集名称
	SeasonNum  int          `json:"SeasonNum"`  //分季序号，从1开始  season_num
	FileSortId int          `json:"FileSortId"` //片集排序号  file_sort_id
	IsShow     int          `json:"IsShow"`     //上下架:1=下架,2=上架  is_show
	PlayUrl    []struct {
		FileUrl      string `json:"FileUrl"`      //文件地址  file_url
		FileType     int    `json:"FileType"`     //类别: 2：普通文件
		VideoQuality string `json:"VideoQuality"` //影片质量,清晰度: "HD"
		LineId       int    `json:"LineId"`
	}

	SrtList []SrtClassModel
}

type SrtClassModel struct {
	LangId  int
	SrtName string
	SrtPath string
}

type LangStruct struct {
	Name   string `json:"Name"` //默认片集语言名称
	LangId int    `json:"LangId"` //1：简体中文，2：繁体中文，3：英文
}
type MovieLangStruct struct {
	MovieName    string `json:"MovieName"`
	MovieSummary string `json:"MovieSummary"`
	LangId       int    `json:"LangId"`
}
