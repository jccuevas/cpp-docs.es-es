---
title: Opciones, Asistente para controles ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.control.options
helpviewer_keywords:
- ATL Control Wizard, options
ms.assetid: 4607c51a-992d-433e-9281-919c6f519a3d
ms.openlocfilehash: 1dd136739162c72d8064deb9b1498794f1985e1b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282986"
---
# <a name="options-atl-control-wizard"></a>Opciones, Asistente para controles ATL

Utilice esta página del Asistente para definir el tipo de control que se va a crear y el nivel de compatibilidad con la interfaz contiene.

## <a name="uielement-list"></a>Lista de UIElement

### <a name="control-type"></a>Tipo de control

El tipo de control que desea crear.

- **Control estándar**: Un control ActiveX.

- **Control compuesto**: Un control ActiveX que puede contener (similar a un cuadro de diálogo) otros controles ActiveX o controles de Windows. Un control compuesto incluye lo siguiente:

  - Una plantilla para el cuadro de diálogo que implementa el control compuesto.

  - Un recurso personalizado, registro, lo que se registra automáticamente el control compuesto cuando se invoca.

  - Una clase de C++ que implementa el control compuesto.

  - Una interfaz COM, expuesta por el control compuesto.

  - Una página de prueba HTML que contiene el control compuesto.

    De forma predeterminada, este control establece [CComControlBase:: M_bwindowonly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) es verdadera, para indicar que se trata de un control con ventana. Implementa un mapa de receptores. Para obtener más información, consulte [compatibilidad con controles DHTML](../../atl/atl-support-for-dhtml-controls.md).

- **Control DHTML**: Un control DHTML ATL especifica la interfaz de usuario mediante HTML. La clase de UI DHTML contiene un mapa COM. De forma predeterminada, este control establece [CComControlBase:: M_bwindowonly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) es verdadera, para indicar que se trata de un control con ventana.

   Para obtener más información, consulte [que identifican los elementos del proyecto de Control DHTML](../../atl/identifying-the-elements-of-the-dhtml-control-project.md).

### <a name="minimal-control"></a>Control mínimo

Sólo admite las interfaces que son absolutamente necesarios por la mayoría de los contenedores. Puede establecer **control mínimo** para cualquiera de los tipos de control: puede crear un control estándar mínimo, un control compuesto mínimo o un control DHTML mínimo.

### <a name="aggregation"></a>Agregación

Agrega compatibilidad con la agregación para el control que se va a crear. Para obtener más información, consulte [agregación](../../atl/aggregation.md).

- **Sí**: Crear un control que se puede agregar.

- **No**: Crear un control que no se puede agregar.

- **Sólo**: Crear un control que solo se puede crear instancias mediante agregación.

### <a name="threading-model"></a>Modelo de subprocesos

Especifica que el modelo de subprocesos utilizados por el control.

- **Single**: El control sólo se ejecutará en el subproceso COM principal.

- **Apartamento**: El control puede crearse en cualquier apartamento de subproceso único. El valor predeterminado.

### <a name="interface"></a>Interfaz

El tipo de interfaz que expone este control en el contenedor.

- **Dual**: Crea una interfaz que expone propiedades y métodos a través de `IDispatch` y directamente a través de VTBL.

- **Personalizada**: Crea una interfaz que expone métodos directamente a través de VTBL.

   Si selecciona **personalizado**, a continuación, puede especificar que el control es **compatible con automatización**. Si selecciona **compatible con automatización**, a continuación, el asistente agrega el [oleautomation](../../windows/oleautomation.md) atributo a la interfaz en el archivo IDL, y la interfaz puede calcularse mediante el contador de referencias universal en oleaut32.dll. Consulte [Marshaling Details](/windows/desktop/com/marshaling-details) en el SDK de Windows para obtener más información.

   Además, si selecciona **compatible con automatización**, a continuación, todos los parámetros de todos los métodos en el control deben ser variantes compatible.

### <a name="support"></a>Compatibilidad

Los conjuntos adicional admiten vario para el control.

- **Puntos de conexión**: Permite a los puntos de conexión para el objeto mediante la realización de derivar de la clase del objeto [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) y permitir que exponga una interfaz de origen.

- **Licencia**: Agrega compatibilidad para el control [licencias](/windows/desktop/com/licensing). Solo se pueden hospedar controles con licencia, si el equipo cliente tiene la licencia correcta.

## <a name="see-also"></a>Vea también

[Asistente para controles ATL](../../atl/reference/atl-control-wizard.md)
