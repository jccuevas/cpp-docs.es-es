---
title: Implementar una interfaz Dual (ATL) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- IDispatchImpl class, implementing dual interfaces
- dual interfaces, implementing
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ae16adcc6743c7e35aae2a4121819a6df50cf4f0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="implementing-a-dual-interface"></a>Implementar una interfaz Dual
Puede implementar una interfaz dual utilizando la [IDispatchImpl](../atl/reference/idispatchimpl-class.md) (clase), que proporciona una implementación predeterminada de la `IDispatch` métodos en una interfaz dual. Para obtener más información, consulta [Implementing the IDispatch Interface](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945).  
  
 Para utilizar esta clase:  
  
-   Defina su interfaz dual en una biblioteca de tipos.  
  
-   Derive la clase de una especialización de `IDispatchImpl` (pasar información acerca de la biblioteca de interfaz y el tipo como los argumentos de plantilla).  
  
-   Agregar una entrada (o entradas) a la asignación de COM para exponer la interfaz dual mediante `QueryInterface`.  
  
-   Implemente la parte vtable de la interfaz en su clase.  
  
-   Asegúrese de que la biblioteca de tipos que contiene la definición de interfaz está disponible para los objetos en tiempo de ejecución.  
  
## <a name="atl-simple-object-wizard"></a>Asistente para objetos simples ATL  
 Si desea crear una nueva interfaz y una nueva clase para su implementación, puede usar el [cuadro de diálogo Agregar clase de ATL](../ide/add-class-dialog-box.md)y, a continuación, el [ATL Simple Object Wizard](../atl/reference/atl-simple-object-wizard.md).  
  
## <a name="implement-interface-wizard"></a>Asistente para implementar interfaces  
 Si tiene una interfaz existente, puede usar el [Asistente para implementar interfaces](../atl/reference/adding-a-new-interface-in-an-atl-project.md) para agregar la clase base necesaria, entradas de mapa COM y las implementaciones de método de esqueleto a una clase existente.  
  
> [!NOTE]
>  Puede que necesite ajustar la clase base generada de forma que los números de versión principal y secundaria de la biblioteca de tipos se pasan como argumentos de plantilla para su `IDispatchImpl` clase base. El Asistente para implementar interfaces no comprueba el número de versión de la biblioteca de tipos.  
  
## <a name="implementing-idispatch"></a>Implementar IDispatch  
 Puede usar un `IDispatchImpl` clase para proporcionar una implementación de una interfaz dispinterface simplemente especificando la entrada adecuada en el mapa COM base (mediante el [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) o [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid) macro) siempre y cuando tenga una biblioteca de tipos que describe una interfaz dual correspondiente. Es bastante habitual para implementar el `IDispatch` la interfaz de esta manera, por ejemplo. El Asistente para objetos simples de ATL y el Asistente para implementar interfaces ambos se supone que va a implementar `IDispatch` de esta manera, por lo que agregará la entrada correspondiente a la asignación.  
  
> [!NOTE]
>  ATL ofrece la [IDispEventImpl](../atl/reference/idispeventimpl-class.md) y [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) clases que le ayudarán a implementar interfaces dispinterface sin necesidad de una biblioteca de tipos que contiene la definición de una interfaz dual compatible.  
  
## <a name="see-also"></a>Vea también  
 [Interfaces duales y ATL](../atl/dual-interfaces-and-atl.md)

