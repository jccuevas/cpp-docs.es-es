---
title: COM + 1.0, Asistente para componentes ATL COM + 1.0 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.mts.options
dev_langs:
- C++
ms.assetid: 2fbe259c-6be1-4d0e-9cfe-721c75c97cb1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a23f148fbdc611c8a11d8116b2e7dff34fc9d8f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="com-10-atl-com-10-component-wizard"></a>COM+ 1.0, Asistente para componentes ATL COM+ 1.0
Use esta página del Asistente para componentes ATL COM + 1.0 para especificar el tipo de interfaz y las interfaces adicionales que se deben admitir.  
  
 Para obtener más información sobre ATL (proyectos) y las clases COM de ATL, vea [componentes de escritorio ATL COM](../../atl/atl-com-desktop-components.md).  
  
 **Interface**  
 Indica el tipo de interfaz sea compatible con el objeto. De forma predeterminada, el objeto admite una interfaz dual.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Doble**|Especifica que el objeto admite una interfaz dual (su tabla vtable posee funciones de interfaz personalizada y enlace tardío `IDispatch` métodos). Permite que los clientes COM y controladores de automatización tener acceso al objeto.|  
|**Custom**|Especifica que el objeto admite una interfaz personalizada (su tabla vtable posee funciones de interfaz personalizada). Una interfaz personalizada puede ser más rápida que una interfaz dual, especialmente en los límites de proceso.<br /><br /> -   **Compatible con automatización** agrega compatibilidad con automatización a la interfaz personalizada. Para los proyectos con atributos, Establece el **oleautomation** atributo en la coclase.|  
  
 **Uno de estos**  
 Indica que los clientes pueden llamar a este componente de forma asincrónica utilizando colas de mensajes. Agrega atributos de componente macro personalizado (TLBATTR_QUEUEABLE, 0) al archivo .h (proyectos con atributos) o al archivo .idl (proyectos sin atributos).  
  
 **Soporte técnico**  
 Indica compatibilidad adicional para el control de control y el objeto de error.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**ISupportErrorInfo**|¡Crea compatibilidad con la [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) interfaz para el objeto pueda devolver información de error al cliente.|  
|**IObjectControl**|Proporciona el acceso a los objetos a los tres [IObjectControl](http://msdn.microsoft.com/library/windows/desktop/ms686474) métodos: [activar](http://msdn.microsoft.com/library/windows/desktop/ms681303), [CanBePooled](http://msdn.microsoft.com/library/windows/desktop/ms684322), y [desactivar](http://msdn.microsoft.com/library/windows/desktop/ms687094).|  
|**IObjectConstruct**|¡Crea compatibilidad con la [IObjectConstruct](http://msdn.microsoft.com/library/windows/desktop/ms680583) interfaz para administrar pasar parámetros de otros objetos o métodos.|  
  
 **Transacción**  
 Indica que el objeto admite transacciones. Incluye el archivo mtxattr.h en el archivo .idl (proyectos sin atributos).  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Compatible**|Especifica que el objeto nunca es la raíz de una secuencia de transacción agregando la custom(TLBATTR_TRANS_SUPPORTED,0) de macro de atributo de componente en el archivo .h (proyectos con atributos) o al archivo .idl (proyectos sin atributos).|  
|**Obligatoria**|Especifica que el objeto puede o no sea la raíz de una secuencia de transacción agregando la custom(TLBATTR_TRANS_REQUIRED,0) de macro de atributo de componente en el archivo .h (proyectos con atributos) o al archivo .idl (proyectos sin atributos).|  
|**No se admite**|Especifica que el objeto excluye las transacciones. Agrega el custom(TLBATTR_TRANS_NOTSUPP,0) de macro de atributo de componente para el archivo .h (proyectos con atributos) o al archivo .idl (proyectos sin atributos).|  
|**Se requiere nueva**|Especifica que el objeto siempre es la raíz de una secuencia de transacción agregando la custom(TLBATTR_TRANS_REQNEW,0) de macro de atributo de componente en el archivo .h (proyectos con atributos) o al archivo .idl (proyectos sin atributos).|  
  
## <a name="see-also"></a>Vea también  
 [Asistente para 1.0 componentes ATL COM +](../../atl/reference/atl-com-plus-1-0-component-wizard.md)   
 [Componente COM + 1.0 ATL](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)

