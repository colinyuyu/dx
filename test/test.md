数据流向：
从syflixOTT后台里添加点播数据，会自动同步到8K 的后台里。
接口：http://syflixapp.iptv10k.com/import/vod/
方式：Post
参数： 
  1）timestamp : 时间戳（秒）
  2）key : md5("3jIOcUbyl9VQ4BAV" + timestamp) 32位大写
  3）data: ImportVod结构体数组的json字符串格式。下面是例子和对应结构体（golang语言的）  
data数据的例子如下：
[{"InputDefLangId":0,"CategoryMainId":112,"SourceType":"vod888","MovieLang":[{"MovieName":"天龙八部","MovieSummary":"aaaaaa","LangId":2},{"MovieName":"Tianlong Eighth Division","MovieSummary":"aaaaaa","LangId":3}],"SourceId":2,"AdminId":0,"MovieName":"天龙八部","MovieSummary":"aaaaaa","PartCount":48,"ImageUrl":"https://bkimg.cdn.bcebos.com/pic/34fae6cd7b899e510fb3213fdcefce33c895d143a7ca","Director":"于荣光","Actor":"杨祐宁,白澍,张天阳,苏青","Lang":"汉语普通话","LangLang":[{"Name":"汉语普通话","LangId":1},{"Name":"漢語普通話","LangId":2},{"Name":"chinese","LangId":3}],"Area":"中国大陆","AreaLang":[{"Name":"中国大陆","LangId":1},{"Name":"中國大陸","LangId":2},{"Name":"Chinese Mainland","LangId":3}],"Label":"武侠剧","LabelLang":[{"Name":"武侠剧","LangId":1},{"Name":"武俠劇","LangId":2},{"Name":"Wu Xia Ju","LangId":3}],"CategroyName":"武侠","CategoryLang":[{"Name":"武侠","LangId":1},{"Name":"武俠","LangId":2},{"Name":"Wu Xia","LangId":3}],"KeywordFirstLetter":"tlbb tianlongbabu Tianlong Eighth Division","PlayDate":"2018","IsShow":1,"UpdateTimeInfo":"","SetsSort":0,"PlayList":[{"PlayLang":[{"Name":"第1集","LangId":1},{"Name":"劇集1","LangId":2},{"Name":"Eposide 1","LangId":3}],"Name":"eposide 1","SeasonNum":0,"FileSortId":1,"IsShow":1,"PlayUrl":[{"FileUrl":"http://www.baidu.com/1.flv","FileType":2,"VideoQuality":"SD","LineId":0}],"SrtList":null},{"PlayLang":[{"Name":"第2集","LangId":1},{"Name":"劇集2","LangId":2},{"Name":"Eposide 2","LangId":3}],"Name":"eposide 2","SeasonNum":0,"FileSortId":2,"IsShow":1,"PlayUrl":[{"FileUrl":"http://www.baidu.com/2.flv","FileType":2,"VideoQuality":"SD","LineId":0}],"SrtList":null},{"PlayLang":[{"Name":"第3集","LangId":1},{"Name":"劇集3","LangId":2},{"Name":"Eposide 3","LangId":3}],"Name":"eposide 3","SeasonNum":0,"FileSortId":3,"IsShow":1,"PlayUrl":[{"FileUrl":"http://www.baidu.com/3.flv","FileType":2,"VideoQuality":"SD","LineId":0}],"SrtList":null},{"PlayLang":[{"Name":"第4集","LangId":1},{"Name":"劇集4","LangId":2},{"Name":"Eposide 4","LangId":3}],"Name":"eposide 4","SeasonNum":0,"FileSortId":4,"IsShow":1,"PlayUrl":[{"FileUrl":"http://www.baidu.com/4.flv","FileType":2,"VideoQuality":"SD","LineId":0}],"SrtList":null},{"PlayLang":[{"Name":"第5集","LangId":1},{"Name":"劇集5","LangId":2},{"Name":"Eposide 5","LangId":3}],"Name":"eposide 5","SeasonNum":0,"FileSortId":5,"IsShow":1,"PlayUrl":[{"FileUrl":"http://www.baidu.com/5.flv","FileType":2,"VideoQuality":"SD","LineId":0}],"SrtList":null},{"PlayLang":[{"Name":"第6集","LangId":1},{"Name":"劇集6","LangId":2},{"Name":"Eposide 6","LangId":3}],"Name":"eposide 6","SeasonNum":0,"FileSortId":6,"IsShow":1,"PlayUrl":[{"FileUrl":"http://www.baidu.com/6.flv","FileType":2,"VideoQuality":"SD","LineId":0}],"SrtList":null},{"PlayLang":[{"Name":"第7集","LangId":1},{"Name":"劇集7","LangId":2},{"Name":"Eposide 7","LangId":3}],"Name":"eposide 7","SeasonNum":0,"FileSortId":7,"IsShow":1,"PlayUrl":[{"FileUrl":"http://www.baidu.com/7.flv","FileType":2,"VideoQuality":"SD","LineId":0}],"SrtList":null},{"PlayLang":[{"Name":"第8集","LangId":1},{"Name":"劇集8","LangId":2},{"Name":"Eposide 8","LangId":3}],"Name":"eposide 8","SeasonNum":0,"FileSortId":8,"IsShow":1,"PlayUrl":[{"FileUrl":"http://www.baidu.com/8.flv","FileType":2,"VideoQuality":"SD","LineId":0}],"SrtList":null},{"PlayLang":[{"Name":"第9集","LangId":1},{"Name":"劇集9","LangId":2},{"Name":"Eposide 9","LangId":3}],"Name":"eposide 9","SeasonNum":0,"FileSortId":9,"IsShow":1,"PlayUrl":[{"FileUrl":"http://www.baidu.com/9.flv","FileType":2,"VideoQuality":"SD","LineId":0}],"SrtList":null}]}]

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
