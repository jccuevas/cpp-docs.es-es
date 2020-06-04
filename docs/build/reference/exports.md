---
title: EXPORTS
ms.date: 09/07/2018
f1_keywords:
- EXPORTS
helpviewer_keywords:
- EXPORTS .def file statement
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
ms.openlocfilehash: 9ede0d3b53c975298dea3d1331bc0fb00ac246b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328254"
---
# <a name="exports"></a>EXPORTS

Presenta una sección de una o varias definiciones de exportación que especifican los nombres o los ordinales exportados de las funciones o los datos. Cada definición debe estar en una línea independiente.

```DEF
EXPORTS
   definition
```

## <a name="remarks"></a>Observaciones

La primera *definición* puede estar `EXPORTS` en la misma línea que la palabra clave o en una línea posterior. El archivo .DEF puede contener una o varias instrucciones `EXPORTS`.

La sintaxis de una *definición* de exportación es:

> *nombrede entrada*\[__=__*internal_name*| \[ **\@***other_module.exported_name*] \[ \[ _ordinal_ \[ **NONAME**] ] **PRIVADO**] \[ **DATOS**]

*entryname* es la función o el nombre de variable que desea exportar. Este es un paso necesario. Si el nombre que exporta difiere del nombre del archivo DLL, especifique el nombre de la exportación en el archivo DLL mediante *internal_name*. Por ejemplo, si la DLL exporta una función `func1` y quiere que los autores de llamadas la usen como `func2`, tendrá que especificar:

```DEF
EXPORTS
   func2=func1
```

Si el nombre que exporta es de algún otro módulo, especifique el nombre de la exportación en el archivo DLL mediante *other_module.exported_name*. Por ejemplo, si la DLL exporta una función `other_module.func1` y quiere que los autores de llamadas la usen como `func2`, tendrá que especificar:

```DEF
EXPORTS
   func2=other_module.func1
```

Si el nombre que exporta es de otro módulo que exporta por ordinal, especifique el ordinal de exportación en el archivo DLL mediante *other_module*. __#__ *ordinal*. Por ejemplo, si el archivo DLL exporta una función desde el otro módulo donde `func2`es ordinal 42 y desea que los llamadores la usen como , especifique:

```DEF
EXPORTS
   func2=other_module.#42
```

Dado que el compilador MSVC utiliza la decoración de nombres *internal_name* para las funciones `extern "C"` C++, debe usar el nombre representativo internal_name o definir las funciones exportadas mediante el código fuente. El compilador también decora las funciones de C\_que usan la convención de\@llamada [__stdcall](../../cpp/stdcall.md) con un prefijo de subrayado ( ) y un sufijo compuesto por el signo at ( ) seguido del número de bytes (en decimal) en la lista de argumentos.

Para buscar los nombres representativos generados por el compilador, utilice la herramienta [DUMPBIN](dumpbin-reference.md) o la opción [/MAP](map-generate-mapfile.md) del vinculador. Los nombres representativos son específicos de cada compilador. Si exporta los nombres representativos en el archivo .DEF, los ejecutables que vinculen a la DLL se deberán compilar con la misma versión del compilador. Así, nos aseguramos de que los nombres representativos del autor de la llamada coincidan con los nombres exportados del archivo .DEF.

Puede usar \@ *ordinal* para especificar que un número, y no el nombre de la función, entra en la tabla de exportación del archivo DLL. Muchas DLL de Windows exportan ordinales para admitir código heredado. En el código de Windows de 16 bits, era habitual usar ordinales, porque con ellos puede ser más fácil minimizar el tamaño de las DLL. No se recomienda exportar funciones por ordinal a menos que los clientes de DLL lo necesiten para la compatibilidad heredada. Dado que el archivo .LIB contendrá la asignación entre el ordinal y la función, puede usar el nombre de la función como lo haría normalmente en los proyectos que usan la DLL.

Mediante el uso de la palabra clave **NONAME** opcional, puede exportar solo por ordinal y reducir el tamaño de la tabla de exportación en el archivo DLL resultante. Sin embargo, si desea usar [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) en el archivo DLL, debe conocer el ordinal porque el nombre no será válido.

La palabra clave opcional **PRIVATE** impide que *entryname* se incluya en la biblioteca de importación generada por LINK. No afecta a la exportación de la imagen que también genera LINK.

La palabra clave opcional **DATA** especifica que una exportación son datos, no código. Este ejemplo le muestra cómo podría exportar una variable de datos llamada `exported_global`:

```DEF
EXPORTS
   exported_global DATA
```

Puede exportar una definición de estas cuatro formas, por orden de más a menos recomendadas:

1. La palabra clave [__declspec(dllexport)](../../cpp/dllexport-dllimport.md) en el código fuente

1. Una instrucción `EXPORTS` en un archivo .DEF

1. Una especificación [/EXPORT](export-exports-a-function.md) en un comando LINK

1. Una directiva [de comentario](../../preprocessor/comment-c-cpp.md) en el `#pragma comment(linker, "/export: definition ")`código fuente, del formulario . En el ejemplo siguiente se muestra una `PlainFuncName` #pragma directiva comment antes `_PlainFuncName@4` de una declaración de función, donde está el nombre no decorado y es el nombre representativo de la función:

    ```cpp
    #pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
    BOOL CALLBACK PlainFuncName( Things * lpParams)
    ```

La directiva #pragma es útil si necesita exportar un nombre de función no decorado y tener exportaciones diferentes en función de la configuración de compilación (por ejemplo, en compilaciones de 32 bits o 64 bits).

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

## <a name="see-also"></a>Consulte también

[Reglas para instrucciones de definición de módulos](rules-for-module-definition-statements.md)
