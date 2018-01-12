---
title: Utilizar ventanas contenidas | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
- contained windows in ATL
ms.assetid: 7b3d79e5-b569-413f-9b98-df4f14efbe2b
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f812b99131d63b87df8dbfd8c9afd5493d0a0140
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-contained-windows"></a>Utilizar ventanas contenidas
ATL implementa las ventanas independientes con [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md). Una ventana contenida representa una ventana que delega sus mensajes en un objeto contenedor en lugar de controlarlos en su propia clase.  
  
> [!NOTE]
>  No es necesario derivar una clase de `CContainedWindowT` para utilizar ventanas contenidas.  
  
 Con windows independientes, puede superclase de una clase Windows existente o crear subclases de una ventana existente. Para crear una ventana de superclase un Windows existentes de clases, especifique primero el nombre de clase existente en el constructor para la `CContainedWindowT` objeto. A continuación, llamar a `CContainedWindowT::Create`. Para crear subclases de una ventana existente, no es necesario especificar un nombre de clase de Windows (pasar **NULL** al constructor). Basta con llamar a la `CContainedWindowT::SubclassWindow` método con el identificador de la ventana que se va a crear subclase.  
  
 Se suele usar windows independientes como miembros de datos de una clase de contenedor. No es necesario que el contenedor sea una ventana; Sin embargo, debe derivar de [CMessageMap](../atl/reference/cmessagemap-class.md).  
  
 Una ventana contenida puede utilizar mapas de mensajes alternativos para controlar sus mensajes. Si tiene más de una ventana contenida, debe declarar que varios mapas de mensajes, cada uno correspondiente a una ventana contenida independiente de alternativos.  
  
## <a name="example"></a>Ejemplo  
 Aquí te mostramos un ejemplo de una clase de contenedor con dos ventanas independientes:  
  
 [!code-cpp[NVC_ATL_Windowing#67](../atl/codesnippet/cpp/using-contained-windows_1.h)]  
  
 Para obtener más información acerca de las ventanas independientes, consulte la [SUBEDIT](../visual-cpp-samples.md) ejemplo.  
  
## <a name="see-also"></a>Vea también  
 [Clases de ventana](../atl/atl-window-classes.md)

