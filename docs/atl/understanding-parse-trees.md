---
title: Registrador de ATL y árboles de análisis
ms.date: 11/04/2016
helpviewer_keywords:
- parse trees
ms.assetid: 668ce2dd-a1c3-4ca0-8135-b25267cb6a85
ms.openlocfilehash: de2cea9b0e7b7c62236f708f9aa8217eaa5df51d
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168701"
---
# <a name="understanding-parse-trees"></a>Descripción de los árboles de análisis

Puede definir uno o más árboles de análisis en el script de registrador, donde cada árbol de análisis tiene el formato siguiente:

> \<clave raíz> {\<expresión del registro>} +

Donde:

> \<clave raíz>:: = HKEY_CLASSES_ROOT | HKEY_CURRENT_USER | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKEY_LOCAL_MACHINE | HKEY_USERS | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKEY_PERFORMANCE_DATA | HKEY_DYN_DATA | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKEY_CURRENT_CONFIG | HKCR | HKCU | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKLM | HKU | HKPD | HKDD | HKCC

> \<expresión del registro>:: \<= agregar clave> | \<Eliminar> de clave

> \<Agregar clave>:: = [**ForceRemove** | **noremove** | **Val**]\<nombre de clave>\<[valor de clave>]\<[{Agregar clave>}]

> \<Eliminar clave>:: = **eliminar**\<nombre de clave>

> \<Nombre de clave>:: = **'**\<alfanumérica>+**'**

> \<> alfanumérica:: = *cualquier carácter que no sea NULL, es decir, ASCII 0*

> \<Valor de clave>:: \<= tipo de \<clave>nombre de clave>

> \<Tipo de clave>:: = **s** | **d**

> \<Valor de clave>:: = **'**\<alfanumérica>**'**

> [!NOTE]
> `HKEY_CLASSES_ROOT`y `HKCR` son equivalentes; `HKEY_CURRENT_USER` y `HKCU` son equivalentes; etc.

Un árbol de análisis puede agregar varias claves y subclaves \<a la clave raíz>. Al hacerlo, mantiene el identificador de una subclave abierto hasta que el analizador haya completado el análisis de todas sus subclaves. Este enfoque es más eficaz que trabajar en una sola clave cada vez, como se observa en el ejemplo siguiente:

```rgs
HKEY_CLASSES_ROOT
{
    'MyVeryOwnKey'
    {
        'HasASubKey'
        {
            'PrettyCool'
        }
    }
}
```

En este caso, el registrador se abre `HKEY_CLASSES_ROOT\MyVeryOwnKey`inicialmente (crea). A continuación, ve `MyVeryOwnKey` que tiene una subclave. En lugar de cerrar la clave `MyVeryOwnKey`en, el registrador conserva el identificador y abre (crea `HasASubKey` ) con este identificador primario. (El registro del sistema puede ser más lento cuando no hay ningún identificador primario abierto). Por lo tanto `HKEY_CLASSES_ROOT\MyVeryOwnKey` , abrir y `HasASubKey` , `MyVeryOwnKey` a continuación, abrir con como elemento `MyVeryOwnKey`primario es `MyVeryOwnKey`más rápido que abrir `MyVeryOwnKey\HasASubKey`, cerrar y, a continuación, abrir.

## <a name="see-also"></a>Consulte también

[Crear scripts de registrador](../atl/creating-registrar-scripts.md)
