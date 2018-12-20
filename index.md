## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/liujingmao/liujingmao-githup.io/edit/master/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```
package huawei.com.sparksql.sparksql

import org.apache.spark.{SparkConf, SparkContext}

object StatURITime {

  // https //todo: labels is not supported//shop159942490.taobao.com/?spm=a217m.8316598.711712.8.426d33d5KRgTIh	[2016-07-17 22:48:19]	75
  // https://blog.csdn.net/qq_24073707/article/details/80665991	[2000-07-05 15:18:40]	66
  def main(args: Array[String]): Unit = {

    val conf = new SparkConf().setAppName("GetURLTime").setMaster("local[2]")

    val spark = new SparkContext(conf)

    val rdd1= spark.textFile("/Users/liujingmao/Downloads/data.txt")

    val rdd2=rdd1.map(line=>{

      val f = line.split("\t")

      val domain_url = f(0).split("https://")(1)

      val tmp=domain_url.split("/")

      val domain=tmp(0)

      val url=domain_url.split(domain)(1)

      val times = f(2)

      ("域名："+domain,("URL："+url,"次数："+times))


    })


    //rdd2.take(100).foreach(println)



    val rdd3 = rdd2.groupBy(_._1)

    rdd3.foreach(println)


    val rdd4= rdd3.mapValues(it=>{

      it.toList.sortBy(_._2).reverse

    })

      //.foreach(println)

  spark.stop()


  }


}



```





# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/liujingmao/liujingmao-githup.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
