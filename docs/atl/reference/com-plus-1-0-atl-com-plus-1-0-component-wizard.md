---
title: "COM+ 1.0, Asistente para componentes ATL COM+ 1.0 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.mts.options"
dev_langs: 
  - "C++"
ms.assetid: 2fbe259c-6be1-4d0e-9cfe-721c75c97cb1
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COM+ 1.0, Asistente para componentes ATL COM+ 1.0
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Use esta página del Asistente para componentes ATL COM\+ 1.0 si desea especificar el tipo de interfaz y las interfaces adicionales que se admitirán.  
  
 Para obtener más información acerca de los proyectos ATL y las clases COM de ATL, vea [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md).  
  
 **Interfaz**  
 Indica el tipo de interfaz que admite el objeto.  De forma predeterminada, el objeto admite una interfaz dual.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Doble**|Especifica que el objeto admite una interfaz doble \(su tabla vtable posee funciones de interfaz personalizada y métodos `IDispatch`de enlace en tiempo de ejecución\).  Permite tanto a clientes COM como a controladores de automatización el acceso al objeto.|  
|**Personalizar**|Especifica que el objeto admite una interfaz personalizada \(su tabla vtable posee funciones de interfaz personalizada\).  Una interfaz personalizada puede ser más rápida que una interfaz doble, en especial entre límites de procesos.<br /><br /> -   **Automation compatible** agrega compatibilidad con automatización a la interfaz personalizada.  Para proyectos con atributos, establece el atributo **oleautomation** en la coclase.|  
  
 **En colas**  
 Indica que los clientes pueden llamar a este componente asincrónicamente mediante colas de mensajes.  Agrega la macro con atributos de componente custom\(TLBATTR\_QUEUEABLE, 0\) al archivo .h \(proyectos con atributos\) o al archivo .idl \(proyectos sin atributos\).  
  
 **Compatibilidad**  
 Indica compatibilidad adicional para el control de errores y el control de objetos.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**ISupportErrorInfo**|Crea compatibilidad con la interfaz [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) para que el objeto pueda devolver información de errores al cliente|  
|**IObjectControl**|Proporciona al objeto el acceso a los tres métodos de [IObjectControl](http://msdn.microsoft.com/library/windows/desktop/ms686474): [Activate](http://msdn.microsoft.com/library/windows/desktop/ms681303), [CanBePooled](http://msdn.microsoft.com/library/windows/desktop/ms684322) y [Deactivate](http://msdn.microsoft.com/library/windows/desktop/ms687094).|  
|**IObjectConstruct**|Crea compatibilidad con la interfaz [IObjectConstruct](http://msdn.microsoft.com/library/windows/desktop/ms680583) para administrar el paso de parámetros desde otros métodos u objetos.|  
  
 **Transacción**  
 Indica que el objeto admite transacciones.  Incluye el archivo mtxattr.h en el archivo .idl \(proyectos sin atributos\).  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Compatible**|Especifica que el objeto nunca actúa como raíz de una secuencia de transacción agregando la macro de atributo de componente custom\(TLBATTR\_TRANS\_SUPPORTED,0\) al archivo .h \(proyectos con atributos\) o al archivo .idl \(proyectos sin atributos\).|  
|**Obligatorio**|Especifica que el objeto puede o no actuar como raíz de una secuencia de transacción agregando la macro de atributo de componente custom\(TLBATTR\_TRANS\_REQUIRED,0\) al archivo .h \(proyectos con atributos\) o al archivo .idl \(proyectos sin atributos\).|  
|**No compatible**|Especifica que el objeto excluye el uso de transacciones.  Agrega la macro de atributos de componente custom\(TLBATTR\_TRANS\_NOTSUPP, 0\) al archivo .h \(proyectos con atributos\) o al archivo .idl \(proyectos sin atributos\).|  
|**Se requiere nueva**|Especifica que el objeto siempre actúa como raíz de una secuencia de transacción agregando la macro de atributo de componente custom\(TLBATTR\_TRANS\_REQNEW,0\) al archivo .h \(proyectos con atributos\) o al archivo .idl \(proyectos sin atributos\).|  
  
## Vea también  
 [Asistente para componentes ATL COM\+ 1.0](../../atl/reference/atl-com-plus-1-0-component-wizard.md)   
 [ATL COM\+ 1.0 Component](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)