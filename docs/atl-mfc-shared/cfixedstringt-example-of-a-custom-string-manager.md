---
title: "CFixedStringT: Example of a Custom String Manager | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFixedStringT class, using a custom string manager"
ms.assetid: 1cf11fd7-51b8-4b94-87af-02bc25f47dd6
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# CFixedStringT: Example of a Custom String Manager
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La biblioteca ATL implementa un ejemplo de un administrador de cadena personalizado utiliza la clase [CFixedStringT](../atl-mfc-shared/reference/cfixedstringt-class.md), denominado **CFixedStringMgr**.  `CFixedStringT` se deriva de [CStringT](../atl-mfc-shared/reference/cstringt-class.md) e implementa una cadena que asigna los datos de caracteres como parte del objeto de `CFixedStringT` propio mientras la cadena es menor que la longitud especificada por el parámetro de plantilla de **t\_nChars** de `CFixedStringT`.  Con este enfoque, string no necesita la pila en absoluto, a menos que la longitud de la cadena aumenta más allá del tamaño del búfer fijo.  Dado que `CFixedStringT` no siempre utiliza una pila para asignar los datos de cadena, no puede utilizar **CAtlStringMgr** como el administrador de la cadena.  Utiliza un administrador de cadena personalizado \(**CFixedStringMgr**\), implementando la interfaz de [IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md) .  Esta interfaz se explica en [Implementación de un administrador de cadena personalizado \(método avanzadas\)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md).  
  
 El constructor de **CFixedStringMgr** toma tres parámetros:  
  
-   Puntero de**pData:** A la estructura fija de `CStringData` que se utilizará.  
  
-   Número máximo de caracteres de**nChars:** The que la estructura de `CStringData` puede contener.  
  
-   Puntero de**pMgr:** A la interfaz de `IAtlStringMgr` “administrador auxiliar de la cadena”.  
  
 El constructor almacena los valores de `pData` y de **pMgr** en las variables miembro respectivas \(`m_pData` y **m\_pMgr**\).  A continuación establece la longitud del búfer a cero, la longitud disponibles igual al tamaño máximo del búfer fijo, y el recuento de referencias – 1.  El valor de recuento de referencias indica que el búfer está bloqueado y utilizar esta instancia de **CFixedStringMgr** como administrador de la cadena.  
  
 Marcar el búfer como bloqueado impide que otras instancias de `CStringT` retengan una referencia compartida en el búfer.  Si otras instancias de `CStringT` se permiten compartir el búfer sería posible para el búfer contenido por `CFixedStringT` que se eliminará mientras otras cadenas todavía utilizaban el búfer.  
  
 **CFixedStringMgr** es una implementación completa de la interfaz de `IAtlStringMgr` .  La implementación de cada método se describe por separado.  
  
## Implementación de CFixedStringMgr::Allocate  
 La implementación de **CFixedStringMgr::Allocate** de comprueba primero para ver si es el tamaño solicitado de la cadena menor o igual que el tamaño de búfer fijo \(almacenado en el miembro de `m_pData` \).  Si el búfer fijo es bastante grande, **CFixedStringMgr** bloquea el búfer fijo con una longitud de cero.  Mientras la longitud de la cadena no aumenta más allá del tamaño del búfer fijo, `CStringT` no tendrá que reasignar el búfer.  
  
 Si el tamaño solicitado de la cadena es mayor que el búfer fijo **CFixedStringMgr** reenvía la solicitud el auxiliar asociado al administrador.  Supone el administrador auxiliar string para asignar el búfer de la pila.  Sin embargo, antes de devolver este búfer **CFixedStringMgr** bloquea el búfer y reemplaza el puntero del administrador de la cadena de búfer con un puntero al objeto de **CFixedStringMgr** .  Esto garantiza que los intentos de reasignar o de liberar el búfer por `CStringT` nombre en **CFixedStringMgr**.  
  
## Implementación de CFixedStringMgr::ReAllocate  
 La implementación de **CFixedStringMgr::ReAllocate** es muy similar a la implementación de **Allocate**.  
  
 Si el búfer que es reasignado es el búfer fijo y el tamaño de búfer solicitado es menor que el búfer fijo, no se realiza ninguna asignación.  Sin embargo, si el búfer que es reasignado no es el búfer fijo, debe ser un búfer asignado con el administrador auxiliar.  En este caso usan el administrador auxiliar para reasignar el búfer.  
  
 Si el búfer que es reasignado es el búfer fijo y el nuevo tamaño de búfer es demasiado grande caber dentro del búfer fijo, **CFixedStringMgr** asigna un nuevo búfer mediante el administrador auxiliar.  El contenido del búfer fijo se copian en el nuevo búfer.  
  
## Implementación de CFixedStringMgr::Free  
 La implementación de **CFixedStringMgr::Free** sigue el mismo modelo que **Allocate** y `ReAllocate`.  Si el búfer que es no es el búfer fijo, el método lo establece en un búfer bloqueado cero\- longitud.  Si el búfer que fue liberado fue asignado con el administrador auxiliar, **CFixedStringMgr** utilizará el administrador auxiliar para liberarlo.  
  
## Implementación de CFixedStringMgr::Clone  
 La implementación de **CFixedStringMgr::Clone** siempre devuelve un puntero al administrador auxiliar en lugar de **CFixedStringMgr** propio.  Esto sucede porque cada instancia de **CFixedStringMgr** solo puede estar asociado a una única instancia de `CStringT`.  Cualquier otra instancia de `CStringT` que intenta clonar el administrador debe obtener el administrador auxiliar en su lugar.  Esto es porque la auxiliares de administrador se compartan.  
  
## Implementación de CFixedStringMgr::GetNilString  
 La implementación de **CFixedStringMgr::GetNilString** devuelve el búfer fijo.  Debido a la correspondencia unívoca de **CFixedStringMgr** y de `CStringT`, una instancia determinada de `CStringT` nunca utiliza más de un búfer al mismo tiempo.  Por consiguiente, una cadena de la nada y un búfer de cadena real nunca se necesitan al mismo tiempo.  
  
 Siempre que el búfer fijo es, ocultarse **CFixedStringMgr** garantiza que se inicializó con una longitud cero.  Esto permite que se utilice como la cadena de la nada.  Como marcado añadido, establece el miembro de `nAllocLength` de búfer fijo siempre al tamaño completo del búfer fijo.  Esto significa que `CStringT` puede llegar a la cadena sin llamar a [IAtlStringMgr::Reallocate](../Topic/IAtlStringMgr::Reallocate.md), incluso para la cadena de la nada.  
  
## Requisitos  
 **encabezado:** cstringt.h  
  
## Vea también  
 [Memory Management with CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)