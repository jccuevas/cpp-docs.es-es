---
title: "Utilizar bibliotecas de importaci&#243;n y archivos de exportaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "exportaciones circulares"
  - "archivos de exportación"
  - "bibliotecas de importación, utilizar"
ms.assetid: 2634256a-8aa5-4495-8c9e-6cde10e4ed76
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Utilizar bibliotecas de importaci&#243;n y archivos de exportaci&#243;n
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cuando un programa \(un archivo ejecutable o un archivo DLL\) exporta a otro programa desde el que también se importa, o si más de dos programas exportan e importan entre sí, los comandos para vincular estos programas deberán permitir exportaciones circulares.  
  
 En una situación en la que no se realizan exportaciones circulares, al vincular un programa que utiliza exportaciones desde otro programa, deberá especificar la biblioteca de importación para el programa exportador.  La biblioteca de importación para el programa exportador se crea cuando se establece un vínculo con dicho programa.  Por tanto, debe vincular el programa exportador antes que el programa importador.  Por ejemplo, si TWO.dll importa desde ONE.dll, primero se debe vincular ONE.dll y obtener la biblioteca de importación ONE.lib.  Después, se especifica ONE.lib al establecer un vínculo con TWO.dll.  Cuando el vinculador crea TWO.dll, también crea su biblioteca de importación, TWO.lib.  Use TWO.lib para vincular los programas que importe desde TWO.dll.  
  
 Sin embargo, en una situación de exportación circular, no es posible vincular todos los programas interdependientes mediante bibliotecas de importación de los otros programas.  En el ejemplo descrito anteriormente, si DOS.dll también exporta a UNO.dll, la biblioteca de importación para DOS.dll no existirá aún cuando se vincule UNO.dll.  Cuando existan exportaciones circulares deberá utilizar LIB para crear una biblioteca de importación y un archivo de exportación para uno de los programas.  
  
 Para empezar, elija uno de los programas en los que se ejecuta LIB.  En el comando LIB, enumere todos los objetos y bibliotecas correspondientes al programa y especifique \/DEF.  Si el programa utiliza un archivo .def o especificaciones \/EXPORT, indíquelo también.  
  
 Después de crear la biblioteca de importación \(.lib\) y el archivo de exportación \(.exp\) para el programa, debe utilizar la biblioteca de importación al vincular los otros programas.  LINK crea una biblioteca de importación para cada programa exportador que compile.  Por ejemplo, si ejecuta LIB en los objetos y las exportaciones para ONE.dll, se crea ONE.lib y ONE.exp.  Entonces puede usar ONE.lib al establecer un vínculo con TWO.dll. En este paso, también se crea la biblioteca de importación TWO.lib.  
  
 Por último, vincule el programa con que empezó.  Especifique en el comando LINK los objetos y las bibliotecas para el programa, el archivo .exp que creó LIB para el programa y las bibliotecas de importación para las exportaciones utilizadas por el programa.  Continuando con el ejemplo, el comando LINK para ONE.dll contiene ONE.exp y TWO.lib, así como los objetos y las bibliotecas que corresponden a ONE.dll.  No indique el archivo .def ni especificaciones \/EXPORT en el comando LINK; no son necesarios, ya que las definiciones de exportación están contenidas en el archivo .exp.  Cuando se vincula con un archivo .exp, LINK no crea una biblioteca de importación, puesto que se da por supuesto que se creó una al crearse el archivo .exp.  
  
## Vea también  
 [Trabajar con bibliotecas de importación y archivos de exportación](../../build/reference/working-with-import-libraries-and-export-files.md)