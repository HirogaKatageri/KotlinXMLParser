# KotlinXMLParser 1.0.4.1 (ported from [Kongsin](https://github.com/kongsin/KotlinXMLParser))
**KotlinXMLParser is a library to map XML to an object or convert an object to XML**

## Features
* Map XML to Object
* Convert Object to XML String
* Stream XML from URL and Map to Object

## How to import

**Add the following in your project's gradle**

    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }

**Add the following in your module's gradle**

    dependencies {
	    implementation 'com.github.HirogaKatageri:KotlinXMLParser:aar-SNAPSHOT'
	}

### XML String is required to map into an object

**Kotlin**

    var xml = "<bookstore>\n" +
        "  <book category=\"children\">\n" +
        "    <title>Harry Potter</title>\n" +
        "    <author>J K. Rowling</author>\n" +
        "    <author>K. Kongsin</author>\n" +
        "    <year>2005</year>\n" +
        "    <price>29.99</price>\n" +
        "  </book>\n" +
        "  <book category=\"web\">\n" +
        "    <title>Learning XML</title>\n" +
        "    <author>Erik T. Ray</author>\n" +
        "    <year>2003</year>\n" +
        "    <price>39.95</price>\n" +
        "  </book>\n" +
        "</bookstore>";

### An Object's name must be the same as the tag name

**Kotlin**

    class Bookstore {
        @JvmField var book: Array<Book>? = null
    }


### Another Object for the book details

**Kotlin**

    class Book {
        @JvmField var title: String? = null
        @JvmField var author: String? = null
        @JvmField var year: String? = null
        @JvmField var price: String? = null
    }

### Here is how you map the XML to an object

**Kotlin**

    var book = XMLParser().fromXML(xml, Bookstore()) as Bookstore

    // Print object to see the result
    book.book!!.forEach {  book ->
        println("---------------------")
        println("TITLE : " + book.title)
        println("AUTHOR : " + book.author)
        println("YEAR : " + book.year)
        println("PRICE : " + book.price)
    }

### Result

    ---------------------
    TITLE : Harry Potter
    AUTHOR : K. Kongsin
    YEAR : 2005
    PRICE : 29.99
    ---------------------
    TITLE : Learning XML
    AUTHOR : Erik T. Ray
    YEAR : 2003
    PRICE : 39.95
