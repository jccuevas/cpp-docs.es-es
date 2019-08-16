---
title: Ejemplos de secuencias de registro
ms.date: 11/04/2016
helpviewer_keywords:
- scripting, examples
- registrar scripts [ATL]
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
ms.openlocfilehash: dffdd111d33d6fbd845e1534cdef1d5c8e1749d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275417"
---
# <a name="registry-scripting-examples"></a>Ejemplos de secuencias de registro

Los ejemplos de secuencias de comandos en este tema muestran cómo agregar una clave al registro del sistema, registrar el servidor COM de registrador y especificar varios árboles de análisis.

## <a name="add-a-key-to-hkeycurrentuser"></a>Agregar una clave a HKEY_CURRENT_USER

El árbol de análisis siguiente muestra un sencillo script que se agrega una clave única al registro del sistema. En concreto, el script agrega la clave, `MyVeryOwnKey`a `HKEY_CURRENT_USER`. También asigna el valor de cadena predeterminado de `HowGoesIt` a la nueva clave:

```
HKEY_CURRENT_USER
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

Este script se puede ampliar fácilmente para definir varias subclaves como sigue:

```
HKCU
{
    'MyVeryOwnKey' = s 'HowGoesIt'
    {
        'HasASubkey'
        {
            'PrettyCool' = d '55'
            val 'ANameValue' = s 'WithANamedValue'
        }
    }
}
```

Ahora, el script agrega una subclave, `HasASubkey`a `MyVeryOwnKey`. Para esta subclave, agrega tanto el `PrettyCool` subclave (su valor predeterminado es `DWORD` valor de 55) y el `ANameValue` valor con nombre (con un valor de cadena de `WithANamedValue`).

##  <a name="_atl_register_the_registrar_com_server"></a> Registrar el servidor COM de registrador

La secuencia de comandos siguiente registra el propio servidor COM de registrador.

```
HKCR
{
    ATL.Registrar = s 'ATL Registrar Class'
    {
        CLSID = s '{44EC053A-400F-11D0-9DCD-00A0C90391D3}'
    }
    NoRemove CLSID
    {
        ForceRemove {44EC053A-400F-11D0-9DCD-00A0C90391D3} = s 'ATL Registrar Class'
        {
            ProgID = s 'ATL.Registrar'
            InprocServer32 = s '%MODULE%'
            {
                val ThreadingModel = s 'Apartment'
            }
        }
    }
}
```

En tiempo de ejecución, este árbol de análisis agrega el `ATL.Registrar` clave a `HKEY_CLASSES_ROOT`. En esta nueva clave, a continuación, la TI:

- Especifica `ATL Registrar Class` como valor de cadena de la clave predeterminada.

- Agrega `CLSID` como subclave.

- Especifica `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` para `CLSID`. (Este valor es el registrador CLSID para su uso con `CoCreateInstance`.)

Puesto que `CLSID` es compartido, no debe eliminarse en el modo de anular el registro. La instrucción, `NoRemove CLSID`, esto se consigue que indica que `CLSID` debe abrirse en modo de registro y omiten en el modo de anular el registro.

El `ForceRemove` instrucción proporciona una función de mantenimiento mediante la eliminación de una clave y todas sus subclaves antes de volver a crear la clave. Esto puede ser útil si han cambiado los nombres de las subclaves. En este ejemplo de scripting, `ForceRemove` comprueba si `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` ya existe. Si es así, `ForceRemove`:

- Elimina de forma recursiva `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` y todas sus subclaves.

- Vuelve a crear `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.

- Agrega `ATL Registrar Class` como el valor de cadena predeterminado para `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.

Ahora, el árbol de análisis agrega dos nuevas subclaves a `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`. La primera clave, `ProgID`, obtiene un valor de cadena predeterminado que es el ProgID. La segunda clave, `InprocServer32`, obtiene un valor de cadena predeterminado, `%MODULE%`, que es un valor de preprocesador se explica en la sección [utilizar parámetros reemplazables (el preprocesador del registrador)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md), de este artículo. `InprocServer32` También obtiene un valor con nombre, `ThreadingModel`, con un valor de cadena de `Apartment`.

## <a name="specify-multiple-parse-trees"></a>Especificar varios árboles de análisis

Para especificar más de un árbol de análisis en una secuencia de comandos, basta con colocar un árbol al final de otro. Por ejemplo, el siguiente script agrega la clave, `MyVeryOwnKey`, los árboles de análisis para ambos `HKEY_CLASSES_ROOT` y `HKEY_CURRENT_USER`:

```
HKCR
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
HKEY_CURRENT_USER
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

> [!NOTE]
> En un script de registrador, 4K es el tamaño máximo del token. (Un token es cualquier elemento reconocible en la sintaxis). En el ejemplo anterior de scripting, `HKCR`, `HKEY_CURRENT_USER`, `'MyVeryOwnKey'`, y `'HowGoesIt'` son todos los tokens.

## <a name="see-also"></a>Vea también

[Crear scripts del registrador](../atl/creating-registrar-scripts.md)
