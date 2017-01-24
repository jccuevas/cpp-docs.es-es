---
title: "EXPORTS | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EXPORTS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EXPORTS (instrucción de archivo .def)"
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# EXPORTS
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Presenta una sección de una o varias definiciones de exportación que especifican los nombres o los ordinales exportados de las funciones o los datos.  Cada definición debe estar en una línea independiente.  
  
```  
EXPORTS  
   definition  
```  
  
## Comentarios  
 La primera `definition` puede estar en la misma línea que la palabra clave `EXPORTS` o en una de las siguientes líneas.  El archivo .DEF puede contener una o varias instrucciones `EXPORTS`.  
  
 La sintaxis de una `definition` de exportación es:  
  
```  
  
entryname[=internalname] [@ordinal [NONAME]] [[PRIVATE] | [DATA]]  
```  
  
 `entryname` es el nombre de la función o la variable que quiere exportar.  Es obligatorio.  Si el nombre que exporta es distinto del nombre que aparece en la DLL, especifique el nombre de la exportación incluido en la DLL con `internalname`.  Por ejemplo, si la DLL exporta una función `func1` y quiere que los autores de llamadas la usen como `func2`, tendrá que especificar:  
  
```  
EXPORTS  
   func2=func1  
```  
  
 Como el compilador de Visual C\+\+ utiliza nombres representativos para las funciones de C\+\+, debe usar el nombre representativo como `entryname` o `internalname`, o definir las funciones exportadas con `extern "C"` en el código fuente.  El compilador también usa funciones de C representativas que emplean la convención de llamada [\_\_stdcall](../../cpp/stdcall.md) con un prefijo de subrayado \(\_\) y un sufijo formado por una arroba \(@\) seguida del número de bytes \(en decimal\) en la lista de argumentos.  
  
 Para buscar los nombres representativos producidos por el compilador, utilice la herramienta [DUMPBIN](../../build/reference/dumpbin-reference.md) o la opción [\/MAP](../../build/reference/map-generate-mapfile.md) del enlazador.  Los nombres representativos son específicos de cada compilador.  Si exporta los nombres representativos en el archivo .DEF, los ejecutables que vinculen a la DLL se deberán compilar con la misma versión del compilador.  Así, nos aseguramos de que los nombres representativos del autor de la llamada coincidan con los nombres exportados del archivo .DEF.  
  
 Puede usar @`ordinal` para especificar que un número, y no el nombre de la función, se introducirá en la tabla de exportación de la DLL.  Muchas DLL de Windows exportan ordinales para admitir código heredado.  En el código de Windows de 16 bits, era habitual usar ordinales, porque con ellos puede ser más fácil minimizar el tamaño de las DLL.  No recomendamos exportar las funciones por ordinales, salvo que los clientes de su DLL lo necesiten para admitir código heredado.  Dado que el archivo .LIB contendrá la asignación entre el ordinal y la función, puede usar el nombre de la función como lo haría normalmente en los proyectos que usan la DLL.  
  
 Con la palabra clave opcional `NONAME`, puede exportar por ordinal solamente y reducir el tamaño de la tabla de exportación en la DLL resultante.  Sin embargo, si quiere usar [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212.aspx) en la DLL, debe conocer el ordinal, porque el nombre no será válido.  
  
 La palabra clave opcional `PRIVATE` impide que `entryname` se incluya en la biblioteca de importación generada por LINK.  No afecta a la exportación de la imagen que también genera LINK.  
  
 La palabra clave opcional `DATA` especifica que una exportación es de datos y no de código.  Este ejemplo le muestra cómo podría exportar una variable de datos llamada `exported_global`:  
  
```  
EXPORTS  
   exported_global DATA  
```  
  
 Puede exportar una definición de estas cuatro formas, por orden de más a menos recomendadas:  
  
1.  La palabra clave [\_\_declspec\(dllexport\)](../../cpp/dllexport-dllimport.md) en el código fuente  
  
2.  Una instrucción `EXPORTS` en un archivo .DEF  
  
3.  Una especificación [\/EXPORT](../../build/reference/export-exports-a-function.md) en un comando de LINK  
  
4.  Una directiva [comment](../../preprocessor/comment-c-cpp.md) en el código fuente, con la forma `#pragma comment(linker, "/export:``definition``")`  
  
 Se pueden utilizar los cuatro métodos en el mismo programa.  Cuando LINK compila un programa que contiene exportaciones, crea también una biblioteca de importación, excepto si se usa un archivo .EXP en la compilación.  
  
 Este es un ejemplo de una sección EXPORTS:  
  
```  
EXPORTS  
   DllCanUnloadNow      @1          PRIVATE  
   DllWindowName = WindowName       DATA  
   DllGetClassObject    @4 NONAME   PRIVATE  
   DllRegisterServer    @7  
   DllUnregisterServer  
```  
  
 Al exportar una variable de una DLL con un archivo .DEF, no es necesario que especifique `__declspec(dllexport)` en la variable.  Sin embargo, en todos los archivos que utilicen la DLL, deberá usar `__declspec(dllimport)` en la declaración de datos.  
  
## Vea también  
 [Reglas para instrucciones de definición de módulos](../../build/reference/rules-for-module-definition-statements.md)