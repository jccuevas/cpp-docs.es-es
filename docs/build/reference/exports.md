---
title: EXPORTACIONES | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EXPORTS
dev_langs:
- C++
helpviewer_keywords:
- EXPORTS .def file statement
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1f9a8e902e42d44ffa292b9f821839b8e948d7a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="exports"></a>EXPORTS
Presenta una sección de una o varias definiciones de exportación que especifican los nombres o los ordinales exportados de las funciones o los datos. Cada definición debe estar en una línea independiente.  
  
```  
EXPORTS  
   definition  
```  
  
## <a name="remarks"></a>Comentarios  
 La primera `definition` puede estar en la misma línea que la palabra clave `EXPORTS` o en una de las siguientes líneas. El archivo .DEF puede contener una o varias instrucciones `EXPORTS`.  
  
 La sintaxis de una `definition` de exportación es:  
  
```  
  
entryname[=internalname] [@ordinal [NONAME]] [[PRIVATE] | [DATA]]  
```  
  
 `entryname` es el nombre de la función o la variable que quiere exportar. Es obligatorio. Si el nombre que exporta es distinto del nombre que aparece en la DLL, especifique el nombre de la exportación incluido en la DLL con `internalname`. Por ejemplo, si la DLL exporta una función `func1` y quiere que los autores de llamadas la usen como `func2`, tendrá que especificar:  
  
```  
EXPORTS  
   func2=func1  
```  
  
 Como el compilador de Visual C++ utiliza nombres representativos para las funciones de C++, debe usar el nombre representativo como `entryname` o `internalname`, o definir las funciones exportadas con `extern "C"` en el código fuente. El compilador también usa funciones de C que utilizan representativas el [__stdcall](../../cpp/stdcall.md) con un prefijo de subrayado (_) y un sufijo formado por la convención de llamada la arroba (@) seguido del número de bytes (en formato decimal) en la lista de argumentos.  
  
 Para buscar los nombres representativos producidos por el compilador, use la [DUMPBIN](../../build/reference/dumpbin-reference.md) herramienta o el vinculador [/MAP](../../build/reference/map-generate-mapfile.md) opción. Los nombres representativos son específicos de cada compilador. Si exporta los nombres representativos en el archivo .DEF, los ejecutables que vinculen a la DLL se deberán compilar con la misma versión del compilador. Así, nos aseguramos de que los nombres representativos del autor de la llamada coincidan con los nombres exportados del archivo .DEF.  
  
 Puede usar @`ordinal` para especificar que un número, y no el nombre de la función, se introducirá en la tabla de exportación de la DLL. Muchas DLL de Windows exportan ordinales para admitir código heredado. En el código de Windows de 16 bits, era habitual usar ordinales, porque con ellos puede ser más fácil minimizar el tamaño de las DLL. No recomendamos exportar las funciones por ordinales, salvo que los clientes de su DLL lo necesiten para admitir código heredado. Dado que el archivo .LIB contendrá la asignación entre el ordinal y la función, puede usar el nombre de la función como lo haría normalmente en los proyectos que usan la DLL.  
  
 Con la palabra clave opcional `NONAME`, puede exportar por ordinal solamente y reducir el tamaño de la tabla de exportación en la DLL resultante. Sin embargo, si desea usar [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212.aspx) en el archivo DLL, debe conocer el ordinal, porque el nombre no será válido.  
  
 La palabra clave opcional `PRIVATE` impide que `entryname` se incluya en la biblioteca de importación generada por LINK. No afecta a la exportación de la imagen que también genera LINK.  
  
 La palabra clave opcional `DATA` especifica que una exportación es de datos y no de código. Este ejemplo le muestra cómo podría exportar una variable de datos llamada `exported_global`:  
  
```  
EXPORTS  
   exported_global DATA  
```  
  
 Puede exportar una definición de estas cuatro formas, por orden de más a menos recomendadas:  
  
1.  El [__declspec (dllexport)](../../cpp/dllexport-dllimport.md) palabra clave en el código fuente  
  
2.  Una instrucción `EXPORTS` en un archivo .DEF  
  
3.  Un [/exportación](../../build/reference/export-exports-a-function.md) especificación en un comando de LINK  
  
4.  A [comentario](../../preprocessor/comment-c-cpp.md) la directiva en el código fuente, del formulario`#pragma comment(linker, "/export: definition ")`  
  
 Se pueden utilizar los cuatro métodos en el mismo programa. Cuando LINK compila un programa que contiene exportaciones, crea también una biblioteca de importación, excepto si se usa un archivo .EXP en la compilación.  
  
 Este es un ejemplo de una sección EXPORTS:  
  
```  
EXPORTS  
   DllCanUnloadNow      @1          PRIVATE  
   DllWindowName = WindowName       DATA  
   DllGetClassObject    @4 NONAME   PRIVATE  
   DllRegisterServer    @7  
   DllUnregisterServer  
```  
  
 Al exportar una variable de una DLL con un archivo .DEF, no es necesario que especifique `__declspec(dllexport)` en la variable. Sin embargo, en todos los archivos que utilicen la DLL, deberá usar `__declspec(dllimport)` en la declaración de datos.  
  
## <a name="see-also"></a>Vea también  
 [Reglas para instrucciones de definición de módulos](../../build/reference/rules-for-module-definition-statements.md)