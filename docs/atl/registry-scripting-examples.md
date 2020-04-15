---
title: Ejemplos de scripting del Registro
ms.date: 11/04/2016
helpviewer_keywords:
- scripting, examples
- registrar scripts [ATL]
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
ms.openlocfilehash: 7bcdb7076982e2f0bd08f4fd82bb45f21e61ef20
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329335"
---
# <a name="registry-scripting-examples"></a>Ejemplos de scripting del Registro

Los ejemplos de scripting de este tema muestran cómo agregar una clave al registro del sistema, registrar el servidor COM del registrador y especificar varios árboles de análisis.

## <a name="add-a-key-to-hkey_current_user"></a>Agregue una clave a HKEY_CURRENT_USER

El siguiente árbol de análisis ilustra un script simple que agrega una sola clave al registro del sistema. En particular, el script agrega `MyVeryOwnKey`la `HKEY_CURRENT_USER`clave, , a . También asigna el valor de `HowGoesIt` cadena predeterminado de a la nueva clave:

```
HKEY_CURRENT_USER
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

Este script se puede ampliar fácilmente para definir varias subclaves de la siguiente manera:

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

Ahora, el script agrega una `HasASubkey`subclave, , a `MyVeryOwnKey`. A esta subclave, agrega `PrettyCool` tanto la subclave `DWORD` (con un valor `ANameValue` predeterminado de 55) `WithANamedValue`como el valor con nombre (con un valor de cadena de ).

## <a name="register-the-registrar-com-server"></a><a name="_atl_register_the_registrar_com_server"></a>Registre el servidor COM del registrador

El siguiente script registra el propio servidor COM del registrador.

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

En tiempo de ejecución, este `ATL.Registrar` árbol `HKEY_CLASSES_ROOT`de análisis agrega la clave a . A esta nueva clave, entonces:

- Especifica `ATL Registrar Class` como valor de cadena predeterminado de la clave.

- Agrega `CLSID` como una subclave.

- Especifica `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` para `CLSID`. (Este valor es el CLSID del `CoCreateInstance`Registrador para su uso con .)

Puesto `CLSID` que se comparte, no se debe quitar en el modo Anular registro. Para ello, `NoRemove CLSID`la instrucción `CLSID` , lo hace indicando que se debe abrir en modo de registro e ignorarse en el modo Anular registro.

La `ForceRemove` instrucción proporciona una función de limpieza quitando una clave y todas sus subclaves antes de volver a crear la clave. Esto puede ser útil si los nombres de las subclaves han cambiado. En este ejemplo `ForceRemove` de scripting, `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` comprueba si ya existe. Si lo `ForceRemove`hace, :

- Elimina de forma `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` recursiva y todas sus subclaves.

- Vuelva a `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`crear .

- Agrega `ATL Registrar Class` como valor de `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`cadena predeterminado para .

El árbol de análisis ahora `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`agrega dos nuevas subclaves a . La primera `ProgID`clave, , obtiene un valor de cadena predeterminado que es el ProgID. La segunda `InprocServer32`clave, , obtiene un `%MODULE%`valor de cadena predeterminado, , que es un valor de preprocesador que se explica en la sección Uso de [parámetros reemplazables (preprocesador del registrador)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md), de este artículo. `InprocServer32`también obtiene un valor `ThreadingModel`con nombre, `Apartment`, con un valor de cadena de .

## <a name="specify-multiple-parse-trees"></a>Especificar varios árboles de análisis

Para especificar más de un árbol de análisis en un script, simplemente coloque un árbol al final de otro. Por ejemplo, el siguiente script `MyVeryOwnKey`agrega la clave, `HKEY_CLASSES_ROOT` , `HKEY_CURRENT_USER`a los árboles de análisis para ambos y :

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
> En un script de registrador, 4K es el tamaño máximo de token. (Un token es cualquier elemento reconocible de la sintaxis.) En el ejemplo `HKCR`de `HKEY_CURRENT_USER` `'MyVeryOwnKey'`scripting `'HowGoesIt'` anterior, , , , y son todos los tokens.

## <a name="see-also"></a>Consulte también

[Creación de scripts de registrador](../atl/creating-registrar-scripts.md)
