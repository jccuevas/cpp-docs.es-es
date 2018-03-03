---
title: 'CFixedStringT: Ejemplo de un administrador de cadenas personalizado | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CFixedStringT class, using a custom string manager
ms.assetid: 1cf11fd7-51b8-4b94-87af-02bc25f47dd6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7164d2313f5610d1d7e56f5449c81ea9e2282981
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cfixedstringt-example-of-a-custom-string-manager"></a>CFixedStringT: Ejemplo de un administrador de cadenas personalizado
La biblioteca ATL implementa un ejemplo de un administrador de cadenas personalizado utilizado por la clase [CFixedStringT](../atl-mfc-shared/reference/cfixedstringt-class.md), llamado **CFixedStringMgr**. `CFixedStringT`se deriva de [CStringT](../atl-mfc-shared/reference/cstringt-class.md) e implementa una cadena que asigna sus datos de caracteres como parte de la `CFixedStringT` propio objeto siempre que la cadena es menor que la longitud especificada por el **t_nChars** parámetro de plantilla de `CFixedStringT`. Con este enfoque, la cadena no necesita el montón en absoluto, a menos que la longitud de la cadena exceda el tamaño del búfer fijo. Dado que `CFixedStringT` no siempre use un montón para asignar sus datos de cadena, no se puede usar **CAtlStringMgr** como su administrador de la cadena. Utiliza un administrador de la cadena personalizada (**CFixedStringMgr**), que implementa el [IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md) interfaz. Esta interfaz se explica en [implementación de un administrador de cadenas personalizado (método avanzado)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md).  
  
 El constructor de **CFixedStringMgr** toma tres parámetros:  
  
-   **pData:** un puntero a la fijo `CStringData` estructura que se usará.  
  
-   **nChars:** el número máximo de caracteres del `CStringData` puede contener la estructura.  
  
-   **pMgr:** un puntero a la `IAtlStringMgr` interfaz de un "Administrador de la cadena de copia de seguridad".  
  
 El constructor almacena los valores de `pData` y **pMgr** en sus respectivas variables miembro (`m_pData` y **m_pMgr**). A continuación, Establece la longitud del búfer en cero, la longitud disponible igual que el tamaño máximo del búfer fijo y el recuento de referencias en -1. El valor de recuento de referencia indica el búfer está bloqueado y usar esta instancia de **CFixedStringMgr** como administrador de cadenas.  
  
 Marcar el búfer como bloqueado impide que otros `CStringT` instancias de que contiene una referencia al búfer compartida. Si otros `CStringT` instancias se pueden compartir el búfer, sería posible para el búfer contenido `CFixedStringT` eliminarse mientras otras cadenas todavía estaban utilizando el búfer.  
  
 **CFixedStringMgr** es una implementación completa de la `IAtlStringMgr` interfaz. La implementación de cada método se trata por separado.  
  
## <a name="implementation-of-cfixedstringmgrallocate"></a>Implementación de CFixedStringMgr:: Allocate  
 La implementación de **CFixedStringMgr:: Allocate** comprueba primero si el tamaño solicitado de la cadena es menor o igual que el tamaño del búfer fijo (almacenado en el `m_pData` miembro). Si el búfer fijo es suficientemente grande, **CFixedStringMgr** bloquea el búfer fijo con una longitud de cero. Siempre y cuando la longitud de cadena no crezca más allá del tamaño del búfer fijo, `CStringT` no tendrá que reasignar el búfer.  
  
 Si el tamaño solicitado de la cadena es mayor que el búfer fijo **CFixedStringMgr** reenvía la solicitud al administrador de cadenas de reserva. El Administrador de la cadena de copia de seguridad se supone que asigne el búfer del montón. Sin embargo, antes de devolver este búfer **CFixedStringMgr** bloquea el búfer y reemplaza el puntero del Administrador de cadena del búfer con un puntero a la **CFixedStringMgr** objeto. Esto garantiza que los intentos de reasignar o liberar el búfer mediante `CStringT` llamará a **CFixedStringMgr**.  
  
## <a name="implementation-of-cfixedstringmgrreallocate"></a>Implementación de CFixedStringMgr:: ReAllocate  
 La implementación de **CFixedStringMgr:: ReAllocate** es muy similar a su implementación de **Allocate**.  
  
 Si el búfer que se está reasignando es el búfer fijo y el tamaño de búfer solicitado es menor que el búfer fijo, no se realiza ninguna asignación. Sin embargo, si el búfer que se está reasignando no es el búfer fijo, debe ser un búfer asignado con el Administrador de copia de seguridad. En este caso, el Administrador de copia de seguridad se utiliza para reasignar el búfer.  
  
 Si el búfer que se está reasignando es el búfer fijo y el nuevo tamaño de búfer es demasiado grande para caber en el búfer fijo, **CFixedStringMgr** asigna un nuevo búfer utilizando el Administrador de copia de seguridad. El contenido del búfer fijo, a continuación, se copia en el nuevo búfer.  
  
## <a name="implementation-of-cfixedstringmgrfree"></a>Implementación de CFixedStringMgr:: Free  
 La implementación de **CFixedStringMgr:: Free** sigue el mismo patrón que **Allocate** y `ReAllocate`. Si el búfer que se está liberando es el búfer fijo, el método establece en un búfer bloqueado de longitud cero. Si el búfer que se está liberando se asignó con el Administrador de copia de seguridad, **CFixedStringMgr** utiliza el Administrador de copia de seguridad para liberarlo.  
  
## <a name="implementation-of-cfixedstringmgrclone"></a>Implementación de CFixedStringMgr:: Clone  
 La implementación de **CFixedStringMgr:: Clone** siempre devuelve un puntero al administrador de copia de seguridad en lugar de la **CFixedStringMgr** propio. Esto sucede porque todas las instancias de **CFixedStringMgr** solo puede asociarse con una sola instancia de `CStringT`. Las demás instancias de `CStringT` intentando clonar el administrador debe obtener el Administrador de copia de seguridad en su lugar. Esto ocurre porque el Administrador de copia de seguridad permite que se va a compartir.  
  
## <a name="implementation-of-cfixedstringmgrgetnilstring"></a>Implementación de CFixedStringMgr:: GetNilString  
 La implementación de **CFixedStringMgr:: GetNilString** devuelve el búfer fijo. Debido a la correspondencia uno a uno de **CFixedStringMgr** y `CStringT`, una instancia determinada de `CStringT` nunca utiliza más de un búfer cada vez. Por lo tanto, una cadena nil y un búfer de cadena real nunca se necesitan al mismo tiempo.  
  
 Cada vez que el búfer fijo no esté en uso, **CFixedStringMgr** garantiza que se inicializa con una longitud de cero. Esto permite que se pueda usar como la cadena de nulo. Como ventaja adicional, el `nAllocLength` miembro del búfer fijo siempre se establece en el tamaño máximo del búfer fijo. Esto significa que `CStringT` puede crecer la cadena sin llamar a [IAtlStringMgr:: ReAllocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate), ni siquiera para la cadena vacía.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** cstringt.h  
  
## <a name="see-also"></a>Vea también  
 [Administración de memoria con CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)

