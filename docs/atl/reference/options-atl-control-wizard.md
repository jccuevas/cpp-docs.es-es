---
title: Opciones, Asistente para controles ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.control.options
helpviewer_keywords:
- ATL Control Wizard, options
ms.assetid: 4607c51a-992d-433e-9281-919c6f519a3d
ms.openlocfilehash: 25db3995687011de5e9cc0a98506cd26f2f1af0b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495451"
---
# <a name="options-atl-control-wizard"></a>Opciones, Asistente para controles ATL

Use esta página del Asistente para definir el tipo de control que está creando y el nivel de compatibilidad de la interfaz que contiene.

## <a name="uielement-list"></a>Lista de UIElement

### <a name="control-type"></a>Tipo de control

El tipo de control que desea crear.

- **Control estándar**: Control ActiveX.

- **Control compuesto**: Control ActiveX que puede contener (similar a un cuadro de diálogo) otros controles ActiveX o controles de Windows. Un control compuesto incluye lo siguiente:

  - Plantilla para el cuadro de diálogo que implementa el control compuesto.

  - Un recurso personalizado, REGISTRY, que registra automáticamente el control compuesto cuando se invoca.

  - Una C++ clase que implementa el control compuesto.

  - Una interfaz COM, expuesta por el control compuesto.

  - Página de prueba HTML que contiene el control compuesto.

    De forma predeterminada, este control establece [CComControlBase:: m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) en true para indicar que se trata de un control con ventana. Implementa una asignación de receptor. Para obtener más información, vea compatibilidad con el [control DHTML](../../atl/atl-support-for-dhtml-controls.md).

- **Control DHTML**: Un control DHTML ATL especifica la interfaz de usuario mediante HTML. La clase de interfaz de usuario DHTML contiene un mapa COM. De forma predeterminada, este control establece [CComControlBase:: m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) en true para indicar que se trata de un control con ventana.

   Para obtener más información, vea [identificar los elementos del proyecto de control DHTML](../../atl/identifying-the-elements-of-the-dhtml-control-project.md).

### <a name="minimal-control"></a>Control mínimo

Solo admite las interfaces que son absolutamente necesarias para la mayoría de los contenedores. Puede establecer un **control mínimo** para cualquiera de los tipos de control: puede crear un control estándar mínimo, un control compuesto mínimo o un control DHTML mínimo.

### <a name="aggregation"></a>Agregación

Agrega compatibilidad de agregación para el control que se está creando. Para obtener más información, vea [agregación](../../atl/aggregation.md).

- **Sí**: Cree un control que se pueda agregar.

- **No**: Cree un control que no se pueda agregar.

- **Solo**: Cree un control del que solo se puedan crear instancias a través de la agregación.

### <a name="threading-model"></a>Modelo de subprocesos

Especifica que el modelo de subprocesos utilizado por el control.

- **Único**: El control solo se ejecutará en el subproceso COM principal.

- **Apartamento**: El control se puede crear en cualquier apartamento de subproceso único. El valor predeterminado.

### <a name="interface"></a>Interfaz

Tipo de interfaz que este control expone al contenedor.

- **Dual**: Crea una interfaz que expone propiedades y métodos mediante `IDispatch` y directamente a través de VTBL.

- **Personalizada**: Crea una interfaz que expone métodos directamente a través de una VTBL.

   Si selecciona **personalizada**, puede especificar que el control sea **compatible con automatización**. Si selecciona **compatible con Automation**, el asistente agrega el atributo [oleautomation](../../windows/oleautomation.md) a la interfaz en el IDL y la serialización universal puede calcular las referencias de la interfaz en oleaut32. dll. Vea los [detalles del cálculo de referencias](/windows/win32/com/marshaling-details) en el Windows SDK para obtener más información.

   Además, si selecciona **compatible con automatización**, todos los parámetros de todos los métodos del control deben ser compatibles con variantes.

### <a name="support"></a>Soporte técnico

Establece compatibilidad adicional adicional para el control.

- **Puntos de conexión**: Habilita los puntos de conexión para el objeto al hacer que la clase del objeto se derive de [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) y permitir que exponga una interfaz de origen.

- Con **licencia**: Agrega compatibilidad con el control para la [concesión de licencias](/windows/win32/com/licensing). Los controles con licencia solo se pueden hospedar si el equipo cliente tiene la licencia correcta.

## <a name="see-also"></a>Vea también

[Asistente para controles ATL](../../atl/reference/atl-control-wizard.md)
