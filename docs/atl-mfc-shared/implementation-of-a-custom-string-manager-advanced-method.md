---
title: Implementación de un administrador de cadenas personalizado (método de avanzadas) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: 64ab7da9-47c1-4c4a-9cd7-4cc37e7f3f57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2dd21ffbaf3e3a6654e23346af39ab401484b1cd
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757239"
---
# <a name="implementation-of-a-custom-string-manager-advanced-method"></a>Implementación de un administrador de cadenas personalizado (método avanzado)

En situaciones especializadas, puede implementar un administrador de la cadena personalizada que algo más que cambiar el montón utilizado para asignar memoria. En esta situación, debe implementar manualmente el [IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md) interfaz como el Administrador de cadenas personalizado.

Para ello, es importante entender primero cómo [CStringT](../atl-mfc-shared/reference/cstringt-class.md) utiliza esa interfaz para administrar sus datos de cadena. Todas las instancias de `CStringT` tiene un puntero a un [CStringData](../atl-mfc-shared/reference/cstringdata-class.md) estructura. Esta estructura de longitud variable contiene información importante acerca de la cadena (por ejemplo, longitud), así como los datos de caracteres reales para la cadena. Cada administrador de cadenas personalizado es responsable de asignar y liberar estas estructuras a petición de `CStringT`.

El `CStringData` estructura consta de cuatro campos:

- [pStringMgr](../atl-mfc-shared/reference/cstringdata-class.md#pstringmgr) este campo apunta a la `IAtlStringMgr` interfaz utilizada para administrar estos datos de cadena. Cuando `CStringT` debe reasignar o liberar el búfer de cadena que se llama a los métodos Reallocate o Free de esta interfaz, pasando el `CStringData` estructura como parámetro. Al asignar un `CStringData` estructura en el Administrador de cadenas, debe establecer este campo para que apunte a su administrador de cadenas personalizado.

- [nDataLength](../atl-mfc-shared/reference/cstringdata-class.md#ndatalength) este campo contiene la longitud de la lógica actual de la cadena almacenada en el búfer sin incluir el carácter nulo final. `CStringT` actualiza este campo cuando cambia la longitud de la cadena. Al asignar un `CStringData` estructura, el Administrador de cadenas debe establecer este campo en cero. Cuando reasigne un `CStringData` estructura, el Administrador de cadenas personalizado debe dejar este campo sin cambios.

- [nAllocLength](../atl-mfc-shared/reference/cstringdata-class.md#nalloclength) este campo contiene el número máximo de caracteres (excepto el carácter nulo final) que se pueden almacenar en este búfer de cadena sin reasignarlo. Cada vez que `CStringT` necesita aumentar la longitud de la lógica de la cadena, en primer lugar comprueba este campo para asegurarse de que hay suficiente espacio en el búfer. Si se produce un error en la comprobación, `CStringT` llama a su administrador de cadenas personalizado para reasignar el búfer. Al asignar o reasignar un `CStringData` estructura, debe establecer este campo en al menos el número de caracteres solicitado en el *nChars* parámetro [pasado IAtlStringMgr:: Allocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#allocate) o [IAtlStringMgr:: ReAllocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate). Si hay más espacio en el búfer que solicitado, puede establecer este valor para reflejar la cantidad de espacio disponible real. Esto permite `CStringT` crezca la cadena para ocupar todo el espacio asignado antes de que vuelva a llamar al administrador de cadenas para reasignar el búfer.

- [nRefs](../atl-mfc-shared/reference/cstringdata-class.md#nrefs) este campo contiene el recuento de referencias actual del búfer de cadena. Si el valor es uno, a continuación, una instancia única de `CStringT` está utilizando el búfer. Además, la instancia se puede leer y modificar el contenido del búfer. Si el valor es mayor que uno, varias instancias de `CStringT` puede usar el búfer. Dado que el búfer de caracteres se comparte, `CStringT` instancias solo pueden leer el contenido del búfer. Para modificar el contenido, `CStringT` primero realiza una copia del búfer. Si el valor es negativo, solo una instancia de `CStringT` está utilizando el búfer. En este caso, se considera el búfer bloqueado. Cuando un `CStringT` instancia utiliza un búfer bloqueado ninguna otra instancia de `CStringT` pueden compartir el búfer. En su lugar, estas instancias de crean una copia del búfer antes de manipular el contenido. Además, el `CStringT` instancia utilizando el búfer bloqueado no intenta compartir el búfer de cualquier otro `CStringT` instancia asignada a él. En este caso, el `CStringT` instancia copia la otra cadena en el búfer bloqueado.

   Al asignar un `CStringData` estructura, debe establecer este campo para reflejar el tipo de uso compartido permitido para el búfer. Para la mayoría de las implementaciones, establezca este valor en uno. Esto permite que el comportamiento típico de uso compartido de copia en escritura. Sin embargo, si el Administrador de cadenas no es compatible con el búfer de cadena de uso compartido, establezca este campo en un estado bloqueado. Esto obliga a `CStringT` solo Use este búfer para la instancia de `CStringT` que se había asignado.

## <a name="see-also"></a>Vea también

[Administración de memoria con CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)

