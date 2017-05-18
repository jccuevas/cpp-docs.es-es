---
title: COM + 1.0, Asistente para componentes ATL COM + 1.0 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.mts.options
dev_langs:
- C++
ms.assetid: 2fbe259c-6be1-4d0e-9cfe-721c75c97cb1
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 36295e5ce296ea6ba982c4ce8cf729bf45860883
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="com-10-atl-com-10-component-wizard"></a>COM+ 1.0, Asistente para componentes ATL COM+ 1.0
Use esta página del Asistente para componentes ATL COM + 1.0 para especificar el tipo de interfaz y las interfaces adicionales compatibles.  
  
 Para obtener más información sobre los proyectos ATL y las clases COM de ATL, vea [componentes de escritorio ATL COM](../../atl/atl-com-desktop-components.md).  
  
 **(Interfaz)**  
 Indica el tipo de interfaz que admite el objeto. De forma predeterminada, el objeto admite una interfaz dual.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Dual**|Especifica que el objeto admite una interfaz doble (su tabla vtable posee funciones de interfaz personalizada y enlace `IDispatch` métodos). Permite que los clientes COM y los controladores de automatización tener acceso al objeto.|  
|**Personalizada**|Especifica que el objeto admite una interfaz personalizada (su tabla vtable posee funciones de interfaz personalizada). Una interfaz personalizada puede ser más rápida que una interfaz dual, especialmente entre límites de procesos.<br /><br /> -   **Compatible con automatización** agrega compatibilidad con automatización a la interfaz personalizada. Para proyectos con atributos, Establece el **oleautomation** atributo en la coclase.|  
  
 **Poner**  
 Indica que los clientes pueden llamar a este componente de forma asincrónica utilizando colas de mensajes. Agrega atributos de componente macro personalizado (TLBATTR_QUEUEABLE, 0) al archivo .h (proyectos con atributos) o al archivo .idl (proyectos sin atributos).  
  
 **Soporte técnico**  
 Indica compatibilidad adicional para el control de control y objeto de error.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**ISupportErrorInfo**|Crea compatibilidad con la [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) interfaz para el objeto pueda devolver información de error al cliente.|  
|**IObjectControl**|Proporciona al objeto el acceso a las tres [IObjectControl](http://msdn.microsoft.com/library/windows/desktop/ms686474) métodos: [activar](http://msdn.microsoft.com/library/windows/desktop/ms681303), [CanBePooled](http://msdn.microsoft.com/library/windows/desktop/ms684322), y [desactivar](http://msdn.microsoft.com/library/windows/desktop/ms687094).|  
|**IObjectConstruct**|Crea compatibilidad con la [IObjectConstruct](http://msdn.microsoft.com/library/windows/desktop/ms680583) interfaz para administrar pasar parámetros desde otros métodos u objetos.|  
  
 **Transacción**  
 Indica que el objeto admite transacciones. Incluye el archivo mtxattr.h en el archivo .idl (proyectos sin atributos).  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Admite**|Especifica que el objeto nunca es la raíz de una secuencia de transacción agregando la custom(TLBATTR_TRANS_SUPPORTED,0) de macro de atributo de componente al archivo .h (proyectos con atributos) o al archivo .idl (proyectos sin atributos).|  
|**Obligatorio**|Especifica que el objeto puede o no puede ser la raíz de una secuencia de transacción agregando la custom(TLBATTR_TRANS_REQUIRED,0) de macro de atributo de componente al archivo .h (proyectos con atributos) o al archivo .idl (proyectos sin atributos).|  
|**No se admite**|Especifica que el objeto excluye las transacciones. Agrega el custom(TLBATTR_TRANS_NOTSUPP,0) de macro de atributo de componente al archivo .h (proyectos con atributos) o al archivo .idl (proyectos sin atributos).|  
|**Se requiere nueva**|Especifica que el objeto siempre es la raíz de una secuencia de transacción agregando la custom(TLBATTR_TRANS_REQNEW,0) de macro de atributo de componente al archivo .h (proyectos con atributos) o al archivo .idl (proyectos sin atributos).|  
  
## <a name="see-also"></a>Vea también  
 [Asistente para 1.0 componentes ATL COM +](../../atl/reference/atl-com-plus-1-0-component-wizard.md)   
 [Componente ATL COM + 1.0](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)


