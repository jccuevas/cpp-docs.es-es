---
title: Ejemplos de scripting del registro
ms.date: 11/04/2016
helpviewer_keywords:
- scripting, examples
- registrar scripts [ATL]
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
ms.openlocfilehash: 0e225ce28309aa619fd9436d8f4b93e60544e86c
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168753"
---
# <a name="registry-scripting-examples"></a>Ejemplos de scripting del registro

En los ejemplos de scripting de este tema se muestra cómo agregar una clave al registro del sistema, registrar el servidor COM del registrador y especificar varios árboles de análisis.

## <a name="add-a-key-to-hkey_current_user"></a>Agregar una clave a HKEY_CURRENT_USER

En el árbol de análisis siguiente se muestra un script simple que agrega una única clave al registro del sistema. En concreto, el script agrega la clave, `MyVeryOwnKey`, a `HKEY_CURRENT_USER`. También asigna el valor de cadena predeterminado de `HowGoesIt` a la nueva clave:

```rgs
HKEY_CURRENT_USER
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

Este script se puede extender fácilmente para definir varias subclaves de la siguiente manera:

```rgs
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

Ahora, el script agrega una subclave `HasASubkey`,, `MyVeryOwnKey`a. Para esta subclave, agrega `PrettyCool` la subclave (con un valor `DWORD` predeterminado de 55) y el `ANameValue` valor con nombre (con un valor de `WithANamedValue`cadena de).

## <a name="register-the-registrar-com-server"></a><a name="_atl_register_the_registrar_com_server"></a>Registrar el servidor COM del registrador

El siguiente script registra el propio servidor COM del registrador.

```rgs
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

En tiempo de ejecución, este árbol de análisis `ATL.Registrar` agrega la `HKEY_CLASSES_ROOT`clave a. A esta nueva clave, entonces:

- Especifica `ATL Registrar Class` como el valor de cadena predeterminado de la clave.

- Agrega `CLSID` como subclave.

- Especifica `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` para `CLSID`. (Este valor es el CLSID del registrador para su `CoCreateInstance`uso con).

Como `CLSID` es compartido, no se debe quitar en modo de anulación del registro. La instrucción, `NoRemove CLSID`, hace esto indicando que `CLSID` debe abrirse en modo de registro y omitirse en modo de anulación del registro.

La `ForceRemove` instrucción proporciona una función de mantenimiento quitando una clave y todas sus subclaves antes de volver a crear la clave. Esto puede ser útil si los nombres de las subclaves han cambiado. En este ejemplo de scripting `ForceRemove` , comprueba si `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` ya existe. Si lo hace, `ForceRemove`:

- Elimina de forma recursiva `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` y todas sus subclaves.

- Vuelve a crear `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.

- Agrega `ATL Registrar Class` como valor de cadena predeterminado para `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.

Ahora, el árbol de análisis agrega dos nuevas subclaves a `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`. La primera clave, `ProgID`, obtiene un valor de cadena predeterminado que es el ProgID. La segunda clave, `InprocServer32`, obtiene un valor de cadena predeterminado `%MODULE%`,, que es un valor de preprocesador que se explica en la sección, [mediante el uso de parámetros reemplazables (el preprocesador del registrador)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)de este artículo. `InprocServer32`también obtiene un valor con nombre `ThreadingModel`,, con un valor de `Apartment`cadena de.

## <a name="specify-multiple-parse-trees"></a>Especificar varios árboles de análisis

Para especificar más de un árbol de análisis en un script, simplemente coloque un árbol al final de otro. Por ejemplo, el siguiente script agrega la clave, `MyVeryOwnKey`, a los árboles de análisis para `HKEY_CLASSES_ROOT` y `HKEY_CURRENT_USER`:

```rgs
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
> En un script de registrador, 4K es el tamaño máximo del token. (Un token es cualquier elemento reconocible en la sintaxis). En el ejemplo de scripting anterior `HKCR`, `HKEY_CURRENT_USER`, `'MyVeryOwnKey'`, y `'HowGoesIt'` son todos los tokens.

## <a name="see-also"></a>Consulte también

[Crear scripts de registrador](../atl/creating-registrar-scripts.md)
