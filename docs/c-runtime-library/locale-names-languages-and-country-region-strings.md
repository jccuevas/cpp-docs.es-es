---
title: "Nombres de configuraci&#243;n regional, idiomas y cadenas de pa&#237;s/regi&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.strings"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "país/región (cadenas)"
  - "localización, configuración regional"
  - "configuraciones regionales"
  - "setlocale (función)"
  - "idioma (cadenas)"
ms.assetid: a0e5a0c5-5602-4da0-b65f-de3d6c8530a2
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# Nombres de configuraci&#243;n regional, idiomas y cadenas de pa&#237;s/regi&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El argumento de `locale` para las funciones `setlocale` y `_create_locale` se puede establecer usando los nombres, los idiomas, los códigos de país o región, y las páginas de códigos de la configuración regional compatibles con la API NLS de Windows. El argumento de `locale` tiene el formato siguiente:  
  
```  
  
locale :: "locale_name"  
        | "language[_country_region[.code_page]]"  
        | ".code_page"  
        | "C"  
        | ""  
        | NULL  
```  
  
 El formato de nombre de la configuración regional; por ejemplo, se prefiere `en-US` para Inglés \(Estados Unidos\) o `bs-Cyrl-BA` para Bosnio \(cirílico, Bosnia\-Herzegovina\). El conjunto de nombres de configuración regional se describe en [Locale Names](http://msdn.microsoft.com/library/windows/desktop/dd373814.aspx) \(Nombres de configuración regional\). Para obtener la lista de nombres de configuración regional admitidos por la versión del sistema operativo Windows, vea la columna **Culture Name** \(Nombre de referencia cultural\) de la página [National Language Support \(NLS\) API Reference](http://msdn.microsoft.com/goglobal/bb896001.aspx) \[Referencia de la API de compatibilidad con el idioma nacional \(NLS\)\]. En este recurso se enumeran las partes de idioma, script y región compatibles de los nombres de configuración regional. Para obtener información sobre nombres de configuración regional compatibles que tienen criterios de ordenación no predeterminados, vea la columna **Locale Name** \(Nombre de configuración regional\) en [Sort Order Identifiers](http://msdn.microsoft.com/library/windows/desktop/dd374060.aspx) \(Identificadores de criterio de ordenación\).  
  
 El formato *idioma*\[\_*país\_región*\[.*página\_de\_códigos*\]\] se almacena en la configuración regional para una categoría cuando se usa una cadena de idioma, o una cadena de idioma y una cadena de país o región, para crear la configuración regional. El conjunto de cadenas de idioma admitidas se describe en [Cadenas de idioma](../c-runtime-library/language-strings.md). La lista de cadenas de país o región admitidas está en [Cadenas de país y región](../c-runtime-library/country-region-strings.md). Si el idioma especificado no está asociado al país o región especificados, en la configuración regional se almacena el idioma predeterminado para el país o región especificados. No se recomienda usar este formato para las cadenas de configuración regional insertadas en código o serializadas en el almacenamiento, ya que es más probable que una actualización del sistema operativo cambie estas cadenas que el formato de nombre de configuración regional.  
  
 La página de códigos es la página de códigos de ANSI\/OEM asociada a la configuración regional. La página de códigos se determina automáticamente al especificar una configuración regional solo por idioma o por idioma y país o región. El valor especial `.ACP` especifica la página de códigos ANSI para el país o región. El valor especial `.OCP` especifica la página de códigos OEM para el país o región. Por ejemplo, si especifica `"Greek_Greece.ACP"` como configuración regional, la configuración regional se almacena como `Greek_Greece.1253` \(página de códigos ANSI del griego\); si especifica `"Greek_Greece.OCP"` como configuración regional, se almacena como `Greek_Greece.737` \(página de códigos OEM del griego\). Para obtener más información sobre las páginas de códigos, vea [Páginas de códigos](../c-runtime-library/code-pages.md). Para obtener la lista de páginas de códigos admitidas en Windows, vea [Code Page Identifiers](http://msdn.microsoft.com/library/windows/desktop/dd317756.aspx) \(Identificadores de páginas de códigos\).  
  
 Si usa solo la página de códigos para especificar la configuración regional, se usan el idioma y el país o región predeterminados del sistema. Por ejemplo, si especifica `".1254"` \(ANSI del turco\) como configuración regional en un sistema configurado para inglés \(Estados Unidos\), la configuración regional que se almacena es `English_United States.1254`. No se recomienda usar este formato, porque podría causar un comportamiento incoherente.  
  
 Un valor `locale` en `C` especifica el entorno compatible con ANSI mínimo para la conversión de C. La configuración regional de `C` supone que cada tipo de datos `char` es de 1 byte y su valor es siempre menor que 256. Si `locale` señala a una cadena vacía, la configuración regional es el entorno nativo definido por la implementación.  
  
 Puede especificar a la vez todas las categorías de configuración regional para las funciones `setlocale` y `_wsetlocale` con la categoría `LC_ALL`. Todas las categorías se pueden establecer en la misma configuración regional. También puede establecer cada categoría por separado mediante un argumento de configuración regional con el siguiente formato:  
  
```  
LC_ALL_specifier :: locale  
        | [LC_COLLATE=locale][;LC_CTYPE=locale][;LC_MONETARY=locale][;LC_NUMERIC=locale][;LC_TIME=locale]  
  
```  
  
 Puede especificar varios tipos de categoría, separados por punto y coma. Los tipos de categoría que no se especifican usan la configuración regional actual. Por ejemplo, este código establece la configuración regional actual para todas las categorías en `de-DE` y, a continuación, establece las categorías `LC_MONETARY` en `en-GB` y `LC_TIME` en `es-ES`:  
  
 `_wsetlocale(LC_ALL, L"de-DE");`  
  
 `_wsetlocale(LC_ALL, L"LC_MONETARY=en-GB;LC_TIME=es-ES");`  
  
## Vea también  
 [Referencia de la biblioteca en tiempo de ejecución de C](../c-runtime-library/c-run-time-library-reference.md)   
 [\_get\_current\_locale](../c-runtime-library/reference/get-current-locale.md)   
 [setlocale, \_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_create\_locale, \_wcreate\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [Cadenas de idioma](../c-runtime-library/language-strings.md)   
 [Cadenas de país y región](../c-runtime-library/country-region-strings.md)