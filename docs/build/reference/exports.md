---
title: EXPORTS
ms.date: 09/07/2018
f1_keywords:
- EXPORTS
helpviewer_keywords:
- EXPORTS .def file statement
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
ms.openlocfilehash: 33b70c680bfc3db24f5326a2027fa9ec4740e3f2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271351"
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

> *entryname*\[__=__*internal_name*|*other_module.exported_name*] \[**\@**_ordinal_ \[**NONAME**] ] \[ \[**PRIVATE**] | \[**DATA**] ]

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

Si es el nombre que exporta desde otro módulo que exporta por ordinal, especifique la exportación 's ordinal en el archivo DLL mediante el uso de *other_module*.__#__ *ordinal*. Por ejemplo, si la DLL exporta una función desde el módulo donde es 42 ordinal y desea que los llamadores usen como `func2`, especificaría:

```DEF
EXPORTS
   func2=other_module.#42
```

Dado que el compilador de MSVC utiliza nombres representativos para C++ funciones, se debe usar el nombre representativo *internal_name* o definir las funciones exportadas mediante `extern "C"` en el código fuente. El compilador también está contenido en las funciones de C que usan el [__stdcall](../../cpp/stdcall.md) con un carácter de subrayado la convención de llamada (\_) prefijo y sufijo se componen de la arroba (\@) seguido del número de bytes (en formato decimal) en el lista de argumentos.

Para buscar los nombres representativos producidos por el compilador, utilice la [DUMPBIN](dumpbin-reference.md) herramienta o el vinculador [/MAP](map-generate-mapfile.md) opción. Los nombres representativos son específicos de cada compilador. Si exporta los nombres representativos en el archivo .DEF, los ejecutables que vinculen a la DLL se deberán compilar con la misma versión del compilador. Así, nos aseguramos de que los nombres representativos del autor de la llamada coincidan con los nombres exportados del archivo .DEF.

Puede usar \@ *ordinal* para especificar que un número y no el nombre de función entra en tabla de exportación del archivo DLL. Muchas DLL de Windows exportan ordinales para admitir código heredado. En el código de Windows de 16 bits, era habitual usar ordinales, porque con ellos puede ser más fácil minimizar el tamaño de las DLL. No recomendamos exportar las funciones por ordinales, salvo que los clientes de su DLL lo necesiten para admitir código heredado. Dado que el archivo .LIB contendrá la asignación entre el ordinal y la función, puede usar el nombre de la función como lo haría normalmente en los proyectos que usan la DLL.

Mediante el uso opcional **NONAME** palabra clave, puede exportar por ordinal solamente y reducir el tamaño de la tabla de exportación en la DLL resultante. Sin embargo, si desea usar [GetProcAddress](/windows/desktop/api/libloaderapi/nf-libloaderapi-getprocaddress) en el archivo DLL, debe conocer el ordinal, porque el nombre no será válido.

La palabra clave opcional **privada** impide *entrada* se incluyan en la biblioteca de importación generada por LINK. No afecta a la exportación de la imagen que también genera LINK.

La palabra clave opcional **datos** especifica que una exportación es de datos, no código. Este ejemplo le muestra cómo podría exportar una variable de datos llamada `exported_global`:

```DEF
EXPORTS
   exported_global DATA
```

Puede exportar una definición de estas cuatro formas, por orden de más a menos recomendadas:

1. El [__declspec (dllexport)](../../cpp/dllexport-dllimport.md) palabra clave en el código fuente

1. Una instrucción `EXPORTS` en un archivo .DEF

1. Un [/EXPORT](export-exports-a-function.md) especificación en un comando LINK

1. Un [comentario](../../preprocessor/comment-c-cpp.md) la directiva en el código fuente, del formulario `#pragma comment(linker, "/export: definition ")`. El ejemplo siguiente muestra una directiva de #pragma comment antes de una declaración de función, donde `PlainFuncName` es el nombre no representativo, y `_PlainFuncName@4` es el nombre representativo de la función:

    ```cpp
    #pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
    BOOL CALLBACK PlainFuncName( Things * lpParams)
    ```

La directiva #pragma es útil si tiene que exportar un nombre de función no representativos y tener exportaciones diferentes dependiendo de la configuración de compilación (por ejemplo, en las compilaciones de 32 bits o 64 bits).

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

[Reglas para instrucciones de definición de módulos](rules-for-module-definition-statements.md)
