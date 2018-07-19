---
title: Implementación de un administrador de cadenas personalizado (método de avanzado) | Documentos de Microsoft
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
ms.openlocfilehash: 23798a4e3c1a5d3c46ea28dec39b37697aae640f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357820"
---
# <a name="implementation-of-a-custom-string-manager-advanced-method"></a>Implementación de un administrador de cadenas personalizado (método avanzado)
En situaciones especializadas, puede implementar un administrador de la cadena personalizada que cambiar algo más que el montón se utiliza para asignar memoria. En esta situación, debe implementar manualmente el [IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md) interfaz como su administrador de cadenas personalizado.  
  
 Para ello, es importante entender primero cómo [CStringT](../atl-mfc-shared/reference/cstringt-class.md) utiliza esa interfaz para administrar sus datos de cadena. Todas las instancias de `CStringT` tiene un puntero a un [CStringData](../atl-mfc-shared/reference/cstringdata-class.md) estructura. Esta estructura de longitud variable contiene información importante acerca de la cadena (por ejemplo, longitud), así como los datos de carácter real de la cadena. Cada administrador de cadenas personalizado es responsable de asignar y liberar estas estructuras a petición del `CStringT`.  
  
 El `CStringData` estructura incluye cuatro campos:  
  
-   [pStringMgr](../atl-mfc-shared/reference/cstringdata-class.md#pstringmgr) este campo apunta a la `IAtlStringMgr` interfaz usada para administrar estos datos de cadena. Cuando `CStringT` debe reasignar o liberar el búfer de cadena que llama a los métodos Reallocate o Free de esta interfaz, pasando el `CStringData` estructura como un parámetro. Al asignar un `CStringData` estructura en el Administrador de cadenas, debe establecer este campo para que apunte a su administrador de cadenas personalizado.  
  
-   [nDataLength](../atl-mfc-shared/reference/cstringdata-class.md#ndatalength) este campo contiene la longitud actual de la lógica de la cadena almacenada en el búfer sin incluir el carácter null final. `CStringT` actualiza este campo cuando cambia la longitud de la cadena. Al asignar un `CStringData` estructura, el Administrador de cadenas debe establecer este campo en cero. Al reasignar un `CStringData` estructura, el Administrador de cadenas personalizado debe dejar este campo sin modificar.  
  
-   [nAllocLength](../atl-mfc-shared/reference/cstringdata-class.md#nalloclength) este campo contiene el número máximo de caracteres (excepto el carácter null final) que se pueden almacenar en el búfer de cadena sin reasignarlo. Cada vez que `CStringT` necesita aumentar la longitud lógica de la cadena, en primer lugar comprueba este campo para asegurarse de que hay suficiente espacio en el búfer. Si se produce un error en la comprobación, `CStringT` llama a su administrador de cadenas personalizado para reasignar el búfer. Al asignar o reasignar una `CStringData` estructura, debe establecer este campo en al menos el número de caracteres solicitado en el **nChars** parámetro [pasado IAtlStringMgr:: Allocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#allocate) o [IAtlStringMgr:: ReAllocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate). Si hay más espacio en el búfer a la solicitada, puede establecer este valor para reflejar la cantidad de espacio disponible real. Esto permite `CStringT` aumente la cadena para rellenar todo el espacio asignado antes de que devuelva la llamada en el Administrador de cadenas para reasignar el búfer.  
  
-   [nRefs](../atl-mfc-shared/reference/cstringdata-class.md#nrefs) este campo contiene el recuento de referencias actual del búfer de cadena. Si el valor es uno, una sola instancia de `CStringT` está utilizando el búfer. Además, la instancia se permite leer y modificar el contenido del búfer. Si el valor es mayor que uno, varias instancias de `CStringT` puede utilizar el búfer. Dado que se comparte el búfer de caracteres, `CStringT` instancias sólo pueden leer el contenido del búfer. Para modificar el contenido, `CStringT` primero realiza una copia del búfer. Si el valor es negativo, solo una instancia de `CStringT` está utilizando el búfer. En este caso, se considera que el búfer bloqueado. Cuando un `CStringT` instancia no está usando un búfer bloqueado ninguna otra instancia de `CStringT` pueden compartir el búfer. En su lugar, estas instancias crean una copia del búfer antes de manipular el contenido. Además, el `CStringT` instancia utilizando el búfer bloqueado no intenta compartir el búfer de cualquier otro `CStringT` instancia asignada a él. En este caso, el `CStringT` instancia copia la otra cadena en el búfer bloqueado.  
  
     Al asignar un `CStringData` estructura, debe establecer este campo para que refleje el tipo de uso compartido que está permitido para el búfer. Para la mayoría de las implementaciones, establezca este valor en uno. Esto permite que el comportamiento típico de uso compartido de copia en escritura. Sin embargo, si el Administrador de cadenas no admite compartir el búfer de cadena, establezca este campo en un estado bloqueado. Esto obliga a `CStringT` solo Use este búfer para la instancia de `CStringT` que asigna.  
  
## <a name="see-also"></a>Vea también  
 [Administración de memoria con CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)

