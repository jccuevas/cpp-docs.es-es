---
title: EXPORTACIONES | Microsoft Docs
ms.custom: ''
ms.date: 08/20/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- EXPORTS
dev_langs:
- C++
helpviewer_keywords:
- EXPORTS .def file statement
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 299d300cb3b2247a4dfa698a53c486bcef6164e3
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894556"
---
# <a name="exports"></a>EXPORTS

Presenta una sección de una o varias definiciones de exportación que especifican los nombres o los ordinales exportados de las funciones o los datos. Cada definición debe estar en una línea independiente.

```DEF
EXPORTS
   definition
```  

## <a name="remarks"></a>Comentarios

La primera *definición* puede estar en la misma línea que el `EXPORTS` palabra clave o en una línea posteriores. El archivo .DEF puede contener una o varias instrucciones `EXPORTS`.

La sintaxis para una exportación *definición* es:

```DEF
entryname[=internal_name|other_module.another_exported_name] [@Ordinal [NONAME]] [[PRIVATE] | [DATA]]
```

*entrada* es el nombre de función o variable que desee exportar. Es obligatorio. Si el nombre que exporta difiere del nombre del archivo DLL, especifique el nombre de la exportación del archivo DLL con *internal_name*. Por ejemplo, si la DLL exporta una función `func1` y quiere que los autores de llamadas la usen como `func2`, tendrá que especificar:

```DEF
EXPORTS
   func2=func1
```

Si es el nombre que exporta desde algún otro módulo, especifique el nombre de la exportación del archivo DLL con *other_module.exported_name*. Por ejemplo, si la DLL exporta una función `other_module.func1` y quiere que los autores de llamadas la usen como `func2`, tendrá que especificar:

```DEF
EXPORTS
   func2=other_module.func1
```

Si es el nombre que exporta desde otro módulo que exporta por ordinal, especifique la exportación 's ordinal en el archivo DLL mediante el uso de *other_module. #ordinal_number*. Por ejemplo, si la DLL exporta una función desde el módulo donde es 42 ordinal y desea que los llamadores usen como `func2`, especificaría:

```DEF
EXPORTS
   func2=other_module.#42
```

Dado que el compilador de Visual C++ utiliza nombres representativos para las funciones de C++, debe usar el nombre representativo de internal_name o definir las funciones exportadas mediante el uso de extern "C" en el código fuente. El compilador también está contenido en las funciones de C que usan el [__stdcall](../../cpp/stdcall.md) con un carácter de subrayado la convención de llamada (\_) prefijo y sufijo se componen de la arroba (\@) seguido del número de bytes (en formato decimal) en el lista de argumentos.

Para buscar los nombres representativos producidos por el compilador, utilice la [DUMPBIN](../../build/reference/dumpbin-reference.md) herramienta o el vinculador [/MAP](../../build/reference/map-generate-mapfile.md) opción. Los nombres representativos son específicos de cada compilador. Si exporta los nombres representativos en el archivo .DEF, los ejecutables que vinculen a la DLL se deberán compilar con la misma versión del compilador. Así, nos aseguramos de que los nombres representativos del autor de la llamada coincidan con los nombres exportados del archivo .DEF.

Puede usar \@ *ordinal* para especificar que un número y no el nombre de función, pasará a la tabla de exportación del archivo DLL. Muchas DLL de Windows exportan ordinales para admitir código heredado. En el código de Windows de 16 bits, era habitual usar ordinales, porque con ellos puede ser más fácil minimizar el tamaño de las DLL. No recomendamos exportar las funciones por ordinales, salvo que los clientes de su DLL lo necesiten para admitir código heredado. Dado que el archivo .LIB contendrá la asignación entre el ordinal y la función, puede usar el nombre de la función como lo haría normalmente en los proyectos que usan la DLL.

Mediante el uso opcional **NONAME** palabra clave, puede exportar por ordinal solamente y reducir el tamaño de la tabla de exportación en la DLL resultante. Sin embargo, si desea usar [GetProcAddress](https://msdn.microsoft.com/library/windows/desktop/ms683212.aspx) en el archivo DLL, debe conocer el ordinal, porque el nombre no será válido.

La palabra clave opcional **privada** impide *entrada* se incluyan en la biblioteca de importación generada por LINK. No afecta a la exportación de la imagen que también genera LINK.

La palabra clave opcional **datos** especifica que una exportación es de datos, no código. Este ejemplo le muestra cómo podría exportar una variable de datos llamada `exported_global`:

```DEF
EXPORTS
   exported_global DATA
```  

Puede exportar una definición de estas cuatro formas, por orden de más a menos recomendadas:

1. El [__declspec (dllexport)](../../cpp/dllexport-dllimport.md) palabra clave en el código fuente

2. Una instrucción `EXPORTS` en un archivo .DEF

3. Un [/EXPORT](../../build/reference/export-exports-a-function.md) especificación en un comando LINK

4. Un [comentario](../../preprocessor/comment-c-cpp.md) la directiva en el código fuente, del formulario `#pragma comment(linker, "/export: definition ")`  

Se pueden utilizar los cuatro métodos en el mismo programa. Cuando LINK compila un programa que contiene exportaciones, crea también una biblioteca de importación, excepto si se usa un archivo .EXP en la compilación.

Este es un ejemplo de una sección EXPORTS:

```DEF
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
