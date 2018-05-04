---
title: Opciones, Asistente para controles ATL | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.control.options
dev_langs:
- C++
helpviewer_keywords:
- ATL Control Wizard, options
ms.assetid: 4607c51a-992d-433e-9281-919c6f519a3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ab1062d32aadc2ec4af68cda8bca02ac1a45a526
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="options-atl-control-wizard"></a>Opciones, Asistente para controles ATL
Inserte aquí "Búsqueda de resumen de los resultados".  
  
 Utilice esta página del Asistente para definir el tipo de control que se va a crear y el nivel de compatibilidad con una interfaz contiene.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Tipo de control**  
 El tipo de control que desea crear.  
  
-   **Control estándar: un control ActiveX.**  
  
-   **Controles compuestos**: un control ActiveX que puede contener (al igual que un cuadro de diálogo) otros controles ActiveX o controles de Windows. Un control compuesto incluye lo siguiente:  
  
    -   Una plantilla para el cuadro de diálogo que implementa el control compuesto.  
  
    -   Un recurso personalizado, REGISTRY, que registra automáticamente el control compuesto cuando se invoca.  
  
    -   Una clase de C++ que implementa el control compuesto.  
  
    -   Una interfaz COM, expuesta por el control compuesto.  
  
    -   Una página de prueba HTML que contiene el control compuesto.  
  
     De forma predeterminada, este control establece [CComControlBase:: M_bwindowonly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) en true, para indicar que se trata de un control con ventanas. Implementa un mapa de receptor. Para obtener más información, consulte [compatibilidad con controles DHTML](../../atl/atl-support-for-dhtml-controls.md).  
  
-   **Control DHTML**: control DHTML ATL An especifica la interfaz de usuario mediante HTML. La clase UI DHTML contiene un mapa COM. De forma predeterminada, este control establece [CComControlBase:: M_bwindowonly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) en true, para indicar que se trata de un control con ventanas.  
  
     Para obtener más información, consulte [identifica los elementos del proyecto de Control DHTML](../../atl/identifying-the-elements-of-the-dhtml-control-project.md).  
  
 **Control mínimo**  
 Sólo admite las interfaces que sea absolutamente son necesarios para la mayoría de los contenedores. Puede establecer **control mínimo** para cualquiera de los tipos de control: puede crear un control estándar mínimo, un control compuesto mínimo o un control DHTML mínimo.  
  
 **Agregación**  
 Agrega compatibilidad con la agregación para el control que se va a crear. Para obtener más información, consulte [agregaciones](../../atl/aggregation.md).  
  
-   **Sí**: crear un control que se puede agregar.  
  
-   **Ya no**: crear un control que no se puede agregar.  
  
-   **Solo**: crear un control que solo se puede crear instancias mediante agregación.  
  
 **Modelo de subprocesos**  
 Especifica que el modelo de subprocesos utilizados por el control.  
  
-   **Solo**: el control sólo se ejecutará en el subproceso COM principal.  
  
-   **Apartamento**: el control puede crearse en cualquier apartamento de subproceso único. El valor predeterminado.  
  
 **Interface**  
 El tipo de interfaz que expone este control al contenedor.  
  
-   **Dual**: crea una interfaz que expone propiedades y métodos a través de `IDispatch` y directamente a través de VTBL.  
  
-   **Personalizado**: crea una interfaz que expone métodos directamente a través de VTBL.  
  
     Si selecciona **personalizado**, a continuación, puede especificar que el control es **compatible con automatización**. Si selecciona **compatible con automatización**, a continuación, el asistente agrega el [oleautomation](../../windows/oleautomation.md) atribuir a la interfaz en el archivo IDL, y se puede serializar la interfaz con el contador de referencias universal en oleaut32.dll. Vea [Marshaling Details](http://msdn.microsoft.com/library/windows/desktop/ms692621) en el SDK de Windows para obtener más información.  
  
     Además, si selecciona **compatible con automatización**, todos los parámetros para todos los métodos en el control deben ser **VARIANT** compatible.  
  
 **Soporte técnico**  
 Establece diversas compatibilidades adicionales para el control.  
  
-   **Puntos de conexión**: habilita puntos de conexión para el objeto mediante la realización de la clase del objeto deriva [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) y permitir que exponga una interfaz de origen.  
  
-   **Licencia**: agrega compatibilidad para el control de [licencias](http://msdn.microsoft.com/library/windows/desktop/ms690543). Solo se pueden hospedar controles con licencia si el equipo cliente tiene la licencia correcta.  
  
## <a name="see-also"></a>Vea también  
 [Asistente para controles ATL](../../atl/reference/atl-control-wizard.md)

