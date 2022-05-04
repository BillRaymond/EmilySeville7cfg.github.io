---
layout: single
title: "My first XML schema!"
date: 2022-04-12 11:15:00 +1000
categories: news schema pascalabcnet
---

# Summary

{% assign left_color = "58158f" -%}
{%- assign right_color = "000000" -%}
{%- assign logo_color = "e9e0ff" -%}

[![repository](https://img.shields.io/badge/Repository-open-{{ right_color }}?labelColor={{ left_color }})][repo]

[repo]: https://github.com/Console-Utils/xml-pascalabcnet-syntax-highlighting-schema


Today I've made my first schema for PascalABC.NET highlighting config:

```xml
<?xml version="1.0"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"
    targetNamespace="https://github.com/Console-Utils/xml-pascalabcnet-syntax-highlighting-schema"
    xmlns="https://github.com/Console-Utils/xml-pascalabcnet-syntax-highlighting-schema"
    elementFormDefault="qualified">

    <xs:simpleType name="name">
        <xs:restriction base="xs:string">
            <xs:minLength value="1"></xs:minLength>
        </xs:restriction>
    </xs:simpleType>
    <xs:simpleType name="extensions">
        <xs:restriction base="xs:string">
            <xs:minLength value="1"></xs:minLength>
        </xs:restriction>
    </xs:simpleType>

    <xs:element name="SyntaxHighlighting">
        <xs:annotation id="root">
            <xs:documentation>Root item</xs:documentation>
        </xs:annotation>
        <xs:complexType>
            <xs:choice minOccurs="0" maxOccurs="unbounded">
                <xs:element name="Properties">
                    <xs:annotation>
                        <xs:documentation>
                            Properties
                        </xs:documentation>
                    </xs:annotation>
                    <xs:complexType>
                        <xs:choice minOccurs="0" maxOccurs="unbounded">
                            <xs:element name="Property">
                                <xs:annotation>
                                    <xs:documentation>A property</xs:documentation>
                                </xs:annotation>
                                <xs:complexType>
                                    <xs:attribute name="name" type="name"></xs:attribute>
                                    <xs:attribute name="value" type="xs:string"></xs:attribute>
                                </xs:complexType>
                            </xs:element>
                        </xs:choice>
                    </xs:complexType>
                </xs:element>
                <xs:element name="Digits">
                    <xs:annotation>
                        <xs:documentation>Digit options</xs:documentation>
                    </xs:annotation>
                    <xs:complexType>
                        <xs:attribute name="name" type="xs:string"></xs:attribute>
                        <xs:attribute name="bold" type="xs:boolean" default="false"></xs:attribute>
                        <xs:attribute name="italic" type="xs:boolean" default="false"></xs:attribute>
                        <xs:attribute name="color" type="xs:string"></xs:attribute>
                    </xs:complexType>
                </xs:element>
                <xs:element name="RuleSets">
                    <xs:annotation>
                        <xs:documentation>Rules</xs:documentation>
                    </xs:annotation>
                    <xs:complexType>
                        <xs:choice minOccurs="0" maxOccurs="unbounded">
                            <xs:element name="RuleSet">
                                <xs:annotation>
                                    <xs:documentation>A rule set</xs:documentation>
                                </xs:annotation>
                                <xs:complexType>
                                    <xs:choice minOccurs="0" maxOccurs="unbounded">
                                        <xs:element name="Delimiters" type="xs:string" default="&lt;&gt;&#x3C;>~!%^*#()-+=|\/{}[]:;&quot;' ,	?.">
                                            <xs:annotation>
                                                <xs:documentation>Delimiters</xs:documentation>
                                            </xs:annotation>
                                        </xs:element>
                                        <xs:element name="Span">
                                            <xs:annotation>
                                                <xs:documentation>Span highlighting</xs:documentation>
                                            </xs:annotation>
                                            <xs:complexType>
                                                <xs:attribute name="name" type="name"></xs:attribute>
                                                <xs:attribute name="rule" type="name"></xs:attribute>
                                                <xs:attribute name="bold" type="xs:boolean" default="false"></xs:attribute>
                                                <xs:attribute name="italic" type="xs:boolean" default="false"></xs:attribute>
                                                <xs:attribute name="color" type="xs:string"></xs:attribute>
                                            </xs:complexType>
                                        </xs:element>
                                        <xs:element name="MarkPrevious">
                                            <xs:annotation>
                                                <xs:documentation>Paired previous item highlighting</xs:documentation>
                                            </xs:annotation>
                                            <xs:complexType>
                                                <xs:attribute name="bold" type="xs:boolean" default="false"></xs:attribute>
                                                <xs:attribute name="italic" type="xs:boolean" default="false"></xs:attribute>
                                                <xs:attribute name="color" type="xs:string"></xs:attribute>
                                            </xs:complexType>
                                        </xs:element>
                                        <xs:element name="MarkFollowing">
                                            <xs:annotation>
                                                <xs:documentation>Paired next item highlighting</xs:documentation>
                                            </xs:annotation>
                                            <xs:complexType>
                                                <xs:attribute name="bold" type="xs:boolean" default="false"></xs:attribute>
                                                <xs:attribute name="italic" type="xs:boolean" default="false"></xs:attribute>
                                                <xs:attribute name="color" type="xs:string"></xs:attribute>
                                            </xs:complexType>
                                        </xs:element>
                                        <xs:element name="KeyWords">
                                            <xs:annotation>
                                                <xs:documentation>Keywords highlighting</xs:documentation>
                                            </xs:annotation>
                                            <xs:complexType>
                                                <xs:choice minOccurs="0" maxOccurs="unbounded">
                                                    <xs:element name="Key">
                                                        <xs:annotation>
                                                            <xs:documentation>A keyword</xs:documentation>
                                                        </xs:annotation>
                                                        <xs:complexType>
                                                            <xs:attribute name="word">
                                                                <xs:simpleType>
                                                                    <xs:restriction base="xs:string">
                                                                        <xs:enumeration value="abstract"></xs:enumeration>
                                                                        <xs:enumeration value="&amp;"></xs:enumeration>
                                                                        <xs:enumeration value="and"></xs:enumeration>
                                                                        <xs:enumeration value="array"></xs:enumeration>
                                                                        <xs:enumeration value="as"></xs:enumeration>
                                                                        <xs:enumeration value="asyncparam"></xs:enumeration>
                                                                        <xs:enumeration value="async"></xs:enumeration>
                                                                        <xs:enumeration value="auto"></xs:enumeration>
                                                                        <xs:enumeration value="begin"></xs:enumeration>
                                                                        <xs:enumeration value="BigInteger"></xs:enumeration>
                                                                        <xs:enumeration value="boolean"></xs:enumeration>
                                                                        <xs:enumeration value="break"></xs:enumeration>
                                                                        <xs:enumeration value="byte"></xs:enumeration>
                                                                        <xs:enumeration value="cardinal"></xs:enumeration>
                                                                        <xs:enumeration value="case"></xs:enumeration>
                                                                        <xs:enumeration value="char"></xs:enumeration>
                                                                        <xs:enumeration value="class"></xs:enumeration>
                                                                        <xs:enumeration value="constructor"></xs:enumeration>
                                                                        <xs:enumeration value="const"></xs:enumeration>
                                                                        <xs:enumeration value="decimal"></xs:enumeration>
                                                                        <xs:enumeration value="default"></xs:enumeration>
                                                                        <xs:enumeration value="destructor"></xs:enumeration>
                                                                        <xs:enumeration value="div"></xs:enumeration>
                                                                        <xs:enumeration value="double"></xs:enumeration>
                                                                        <xs:enumeration value="downto"></xs:enumeration>
                                                                        <xs:enumeration value="do"></xs:enumeration>
                                                                        <xs:enumeration value="else"></xs:enumeration>
                                                                        <xs:enumeration value="end"></xs:enumeration>
                                                                        <xs:enumeration value="event"></xs:enumeration>
                                                                        <xs:enumeration value="except"></xs:enumeration>
                                                                        <xs:enumeration value="exit"></xs:enumeration>
                                                                        <xs:enumeration value="explicit"></xs:enumeration>
                                                                        <xs:enumeration value="extensionmethod"></xs:enumeration>
                                                                        <xs:enumeration value="external"></xs:enumeration>
                                                                        <xs:enumeration value="false"></xs:enumeration>
                                                                        <xs:enumeration value="file"></xs:enumeration>
                                                                        <xs:enumeration value="finalization"></xs:enumeration>
                                                                        <xs:enumeration value="finally"></xs:enumeration>
                                                                        <xs:enumeration value="foreach"></xs:enumeration>
                                                                        <xs:enumeration value="forward"></xs:enumeration>
                                                                        <xs:enumeration value="for"></xs:enumeration>
                                                                        <xs:enumeration value="function"></xs:enumeration>
                                                                        <xs:enumeration value="goto"></xs:enumeration>
                                                                        <xs:enumeration value="&gt;"></xs:enumeration>
                                                                        <xs:enumeration value="&gt;="></xs:enumeration>
                                                                        <xs:enumeration value="if"></xs:enumeration>
                                                                        <xs:enumeration value="implementation"></xs:enumeration>
                                                                        <xs:enumeration value="implicit"></xs:enumeration>
                                                                        <xs:enumeration value="inherited"></xs:enumeration>
                                                                        <xs:enumeration value="initialization"></xs:enumeration>
                                                                        <xs:enumeration value="int16"></xs:enumeration>
                                                                        <xs:enumeration value="int32"></xs:enumeration>
                                                                        <xs:enumeration value="int64"></xs:enumeration>
                                                                        <xs:enumeration value="integer"></xs:enumeration>
                                                                        <xs:enumeration value="interface"></xs:enumeration>
                                                                        <xs:enumeration value="internal"></xs:enumeration>
                                                                        <xs:enumeration value="in"></xs:enumeration>
                                                                        <xs:enumeration value="is"></xs:enumeration>
                                                                        <xs:enumeration value="label"></xs:enumeration>
                                                                        <xs:enumeration value="library"></xs:enumeration>
                                                                        <xs:enumeration value="lock"></xs:enumeration>
                                                                        <xs:enumeration value="longint"></xs:enumeration>
                                                                        <xs:enumeration value="longword"></xs:enumeration>
                                                                        <xs:enumeration value="loop"></xs:enumeration>
                                                                        <xs:enumeration value="&lt;"></xs:enumeration>
                                                                        <xs:enumeration value="&lt;="></xs:enumeration>
                                                                        <xs:enumeration value="match"></xs:enumeration>
                                                                        <xs:enumeration value="mod"></xs:enumeration>
                                                                        <xs:enumeration value="namespace"></xs:enumeration>
                                                                        <xs:enumeration value="new"></xs:enumeration>
                                                                        <xs:enumeration value="nil"></xs:enumeration>
                                                                        <xs:enumeration value="not"></xs:enumeration>
                                                                        <xs:enumeration value="object"></xs:enumeration>
                                                                        <xs:enumeration value="of"></xs:enumeration>
                                                                        <xs:enumeration value="on"></xs:enumeration>
                                                                        <xs:enumeration value="operator"></xs:enumeration>
                                                                        <xs:enumeration value="or"></xs:enumeration>
                                                                        <xs:enumeration value="overload"></xs:enumeration>
                                                                        <xs:enumeration value="override"></xs:enumeration>
                                                                        <xs:enumeration value="params"></xs:enumeration>
                                                                        <xs:enumeration value="partial"></xs:enumeration>
                                                                        <xs:enumeration value="pointer"></xs:enumeration>
                                                                        <xs:enumeration value="private"></xs:enumeration>
                                                                        <xs:enumeration value="procedure"></xs:enumeration>
                                                                        <xs:enumeration value="program"></xs:enumeration>
                                                                        <xs:enumeration value="property"></xs:enumeration>
                                                                        <xs:enumeration value="protected"></xs:enumeration>
                                                                        <xs:enumeration value="public"></xs:enumeration>
                                                                        <xs:enumeration value="raise"></xs:enumeration>
                                                                        <xs:enumeration value="read"></xs:enumeration>
                                                                        <xs:enumeration value="real"></xs:enumeration>
                                                                        <xs:enumeration value="record"></xs:enumeration>
                                                                        <xs:enumeration value="reintroduce"></xs:enumeration>
                                                                        <xs:enumeration value="repeat"></xs:enumeration>
                                                                        <xs:enumeration value="result"></xs:enumeration>
                                                                        <xs:enumeration value="sbyte"></xs:enumeration>
                                                                        <xs:enumeration value="sealed"></xs:enumeration>
                                                                        <xs:enumeration value="self"></xs:enumeration>
                                                                        <xs:enumeration value="sequence"></xs:enumeration>
                                                                        <xs:enumeration value="set"></xs:enumeration>
                                                                        <xs:enumeration value="shl"></xs:enumeration>
                                                                        <xs:enumeration value="shortint"></xs:enumeration>
                                                                        <xs:enumeration value="shr"></xs:enumeration>
                                                                        <xs:enumeration value="single"></xs:enumeration>
                                                                        <xs:enumeration value="sizeof"></xs:enumeration>
                                                                        <xs:enumeration value="smallint"></xs:enumeration>
                                                                        <xs:enumeration value="static"></xs:enumeration>
                                                                        <xs:enumeration value="string"></xs:enumeration>
                                                                        <xs:enumeration value="then"></xs:enumeration>
                                                                        <xs:enumeration value="to"></xs:enumeration>
                                                                        <xs:enumeration value="true"></xs:enumeration>
                                                                        <xs:enumeration value="try"></xs:enumeration>
                                                                        <xs:enumeration value="typeof"></xs:enumeration>
                                                                        <xs:enumeration value="type"></xs:enumeration>
                                                                        <xs:enumeration value="uint16"></xs:enumeration>
                                                                        <xs:enumeration value="uint32"></xs:enumeration>
                                                                        <xs:enumeration value="uint64"></xs:enumeration>
                                                                        <xs:enumeration value="unit"></xs:enumeration>
                                                                        <xs:enumeration value="until"></xs:enumeration>
                                                                        <xs:enumeration value="uses"></xs:enumeration>
                                                                        <xs:enumeration value="value"></xs:enumeration>
                                                                        <xs:enumeration value="var"></xs:enumeration>
                                                                        <xs:enumeration value="virtual"></xs:enumeration>
                                                                        <xs:enumeration value="when"></xs:enumeration>
                                                                        <xs:enumeration value="where"></xs:enumeration>
                                                                        <xs:enumeration value="while"></xs:enumeration>
                                                                        <xs:enumeration value="with"></xs:enumeration>
                                                                        <xs:enumeration value="word"></xs:enumeration>
                                                                        <xs:enumeration value="write"></xs:enumeration>
                                                                        <xs:enumeration value="xor"></xs:enumeration>
                                                                        <xs:enumeration value="("></xs:enumeration>
                                                                        <xs:enumeration value=")"></xs:enumeration>
                                                                        <xs:enumeration value="*"></xs:enumeration>
                                                                        <xs:enumeration value="+"></xs:enumeration>
                                                                        <xs:enumeration value=","></xs:enumeration>
                                                                        <xs:enumeration value="-"></xs:enumeration>
                                                                        <xs:enumeration value="."></xs:enumeration>
                                                                        <xs:enumeration value="/"></xs:enumeration>
                                                                        <xs:enumeration value=";"></xs:enumeration>
                                                                        <xs:enumeration value="="></xs:enumeration>
                                                                        <xs:enumeration value="["></xs:enumeration>
                                                                        <xs:enumeration value="]"></xs:enumeration>
                                                                        <xs:enumeration value="^"></xs:enumeration>
                                                                        <xs:enumeration value="yield"></xs:enumeration>
                                                                    </xs:restriction>
                                                                </xs:simpleType>
                                                            </xs:attribute>
                                                        </xs:complexType>
                                                    </xs:element>
                                                </xs:choice>
                                                <xs:attribute name="name" type="name"></xs:attribute>
                                                <xs:attribute name="bold" type="xs:boolean" default="false"></xs:attribute>
                                                <xs:attribute name="italic" type="xs:boolean" default="false"></xs:attribute>
                                                <xs:attribute name="color" type="xs:string"></xs:attribute>
                                            </xs:complexType>
                                        </xs:element>
                                    </xs:choice>
                                </xs:complexType>
                            </xs:element>
                        </xs:choice>
                    </xs:complexType>
                </xs:element>
            </xs:choice>
            <xs:attribute name="name" type="name" default="PascalABC.NET-KH"></xs:attribute>
            <xs:attribute name="extensions" type="extensions" default=".pas;.paspart_"></xs:attribute>
        </xs:complexType>
    </xs:element>
</xs:schema>
```

It may not work correctly due to the lack of the documentation for the syntax highlighting setup.
