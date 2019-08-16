---
title: EXPORTS
ms.date: 09/07/2018
f1_keywords:
- EXPORTS
helpviewer_keywords:
- EXPORTS .def file statement
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
ms.openlocfilehash: 8338f27d35d3779a55b83b70c7a3eef285a91f46
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492882"
---
# <a name="exports"></a>EXPORTS

Presenta una sección de una o varias definiciones de exportación que especifican los nombres o los ordinales exportados de las funciones o los datos. Cada definición debe estar en una línea independiente.

```DEF
EXPORTS
   definition
```

## <a name="remarks"></a>Comentarios

La primera *definición* puede estar en la misma línea que la `EXPORTS` palabra clave o en una línea posterior. El archivo .DEF puede contener una o varias instrucciones `EXPORTS`.

La sintaxis de una *definición* de exportación es:

> *nombreentrada* *internal_name other_module. exported_name*] ordinal\[Noname] ]\[ **\@** |\[ __=__ \[ \[ **Privado**] | **Datos]** ] \[

*entryname* es el nombre de la función o variable que desea exportar. Es obligatorio. Si el nombre que exporta difiere del nombre del archivo DLL, especifique el nombre de la exportación en el archivo DLL mediante *internal_name*. Por ejemplo, si la DLL exporta una función `func1` y quiere que los autores de llamadas la usen como `func2`, tendrá que especificar:

```DEF
EXPORTS
   func2=func1
```

Si el nombre que exporta es de otro módulo, especifique el nombre de la exportación en el archivo DLL mediante *other_module. exported_name*. Por ejemplo, si la DLL exporta una función `other_module.func1` y quiere que los autores de llamadas la usen como `func2`, tendrá que especificar:

```DEF
EXPORTS
   func2=other_module.func1
```

Si el nombre que exporta procede de otro módulo que exporta por ordinal, especifique el ordinal de la exportación en el archivo DLL mediante *other_module*. __#__ *ordinal*. Por ejemplo, si el archivo dll exporta una función desde el otro módulo donde es el ordinal 42 y desea que los autores de la llamada lo `func2`utilicen como, debe especificar:

```DEF
EXPORTS
   func2=other_module.#42
```

Dado que el compilador MSVC usa C++ la decoración de nombres para las funciones, debe utilizar el nombre representativo *internal_name* o `extern "C"` definir las funciones exportadas mediante en el código fuente. El compilador también decora las funciones de C que usan la Convención de llamada [_ _ Stdcall](../../cpp/stdcall.md) con un prefijo de subrayado (\_) y un sufijo compuesto por el signo de arroba (\@) seguido del número de bytes (en formato decimal) en la lista de argumentos.

Para buscar los nombres representativos generados por el compilador, use la herramienta [dumpbin](dumpbin-reference.md) o la opción [/map](map-generate-mapfile.md) del vinculador. Los nombres representativos son específicos de cada compilador. Si exporta los nombres representativos en el archivo .DEF, los ejecutables que vinculen a la DLL se deberán compilar con la misma versión del compilador. Así, nos aseguramos de que los nombres representativos del autor de la llamada coincidan con los nombres exportados del archivo .DEF.

Puede usar \@el *ordinal* para especificar que un número, y no el nombre de función, va a la tabla de exportación del archivo dll. Muchas DLL de Windows exportan ordinales para admitir código heredado. En el código de Windows de 16 bits, era habitual usar ordinales, porque con ellos puede ser más fácil minimizar el tamaño de las DLL. No recomendamos exportar las funciones por ordinales, salvo que los clientes de su DLL lo necesiten para admitir código heredado. Dado que el archivo .LIB contendrá la asignación entre el ordinal y la función, puede usar el nombre de la función como lo haría normalmente en los proyectos que usan la DLL.

Mediante el uso de la palabra clave opcional Noname, solo puede exportar por ordinal y reducir el tamaño de la tabla de exportación en el archivo dll resultante. Sin embargo, si desea utilizar [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) en el archivo dll, debe conocer el ordinal porque el nombre no será válido.

La palabra clave **Private** opcional evita que se incluya *entryname* en la biblioteca de importación generada por Link. No afecta a la exportación de la imagen que también genera LINK.

Los **datos** de palabra clave opcionales especifican que una exportación es datos, no código. Este ejemplo le muestra cómo podría exportar una variable de datos llamada `exported_global`:

```DEF
EXPORTS
   exported_global DATA
```

Puede exportar una definición de estas cuatro formas, por orden de más a menos recomendadas:

1. La palabra clave [_ _ declspec (dllexport)](../../cpp/dllexport-dllimport.md) en el código fuente

1. Una instrucción `EXPORTS` en un archivo .DEF

1. Una especificación [/Export](export-exports-a-function.md) en un comando Link

1. Una directiva de [Comentario](../../preprocessor/comment-c-cpp.md) en el código fuente, con el `#pragma comment(linker, "/export: definition ")`formato. En el ejemplo siguiente se muestra una directiva de comentario de #pragma antes de `PlainFuncName` una declaración de función, donde es `_PlainFuncName@4` el nombre no representativo y es el nombre representativo de la función:

    ```cpp
    #pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
    BOOL CALLBACK PlainFuncName( Things * lpParams)
    ```

La Directiva #pragma es útil si necesita exportar un nombre de función no representativo y tiene distintas exportaciones dependiendo de la configuración de compilación (por ejemplo, en compilaciones de 32 bits o de 64 bits).

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
