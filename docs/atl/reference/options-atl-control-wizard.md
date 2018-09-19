---
title: Opciones, Asistente para controles ATL | Microsoft Docs
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
ms.openlocfilehash: 25116b0750016fdbb4ffd792d0b16efb6c6c1793
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711956"
---
# <a name="options-atl-control-wizard"></a>Opciones, Asistente para controles ATL

Inserte aquí "Resultados de búsqueda" resumen.

Utilice esta página del Asistente para definir el tipo de control que se va a crear y el nivel de compatibilidad con la interfaz contiene.

## <a name="uielement-list"></a>Lista de UIElement

### <a name="control-type"></a>Tipo de control

El tipo de control que desea crear.

- **Control estándar**: un control ActiveX.

- **Control compuesto**: un control ActiveX que puede contener (similar a un cuadro de diálogo) otros controles ActiveX o controles de Windows. Un control compuesto incluye lo siguiente:

   - Una plantilla para el cuadro de diálogo que implementa el control compuesto.

   - Un recurso personalizado, registro, lo que se registra automáticamente el control compuesto cuando se invoca.

   - Una clase de C++ que implementa el control compuesto.

   - Una interfaz COM, expuesta por el control compuesto.

   - Una página de prueba HTML que contiene el control compuesto.

     De forma predeterminada, este control establece [CComControlBase:: M_bwindowonly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) es verdadera, para indicar que se trata de un control con ventana. Implementa un mapa de receptores. Para obtener más información, consulte [compatibilidad con controles DHTML](../../atl/atl-support-for-dhtml-controls.md).

- **Control DHTML**: control DHTML ATL An especifica la interfaz de usuario mediante HTML. La clase de UI DHTML contiene un mapa COM. De forma predeterminada, este control establece [CComControlBase:: M_bwindowonly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) es verdadera, para indicar que se trata de un control con ventana.

     Para obtener más información, consulte [que identifican los elementos del proyecto de Control DHTML](../../atl/identifying-the-elements-of-the-dhtml-control-project.md).

### <a name="minimal-control"></a>Control mínimo

Sólo admite las interfaces que son absolutamente necesarios por la mayoría de los contenedores. Puede establecer **control mínimo** para cualquiera de los tipos de control: puede crear un control estándar mínimo, un control compuesto mínimo o un control DHTML mínimo.

### <a name="aggregation"></a>Agregación

Agrega compatibilidad con la agregación para el control que se va a crear. Para obtener más información, consulte [agregación](../../atl/aggregation.md).

- **Sí**: crear un control que se puede agregar.

- **No**: crear un control que no se puede agregar.

- **Sólo**: crear un control que solo se puede crear instancias mediante agregación.

### <a name="threading-model"></a>Modelo de subprocesos

Especifica que el modelo de subprocesos utilizados por el control.

- **Solo**: el control sólo se ejecutará en el subproceso COM principal.

- **Apartamento**: el control puede crearse en cualquier apartamento de subproceso único. El valor predeterminado.

### <a name="interface"></a>Interfaz

El tipo de interfaz que expone este control en el contenedor.

- **Dual**: crea una interfaz que expone propiedades y métodos a través de `IDispatch` y directamente a través de VTBL.

- **Custom**: crea una interfaz que expone métodos directamente a través de VTBL.

   Si selecciona **personalizado**, a continuación, puede especificar que el control es **compatible con automatización**. Si selecciona **compatible con automatización**, a continuación, el asistente agrega el [oleautomation](../../windows/oleautomation.md) atributo a la interfaz en el archivo IDL, y la interfaz puede calcularse mediante el contador de referencias universal en oleaut32.dll. Consulte [Marshaling Details](/windows/desktop/com/marshaling-details) en el SDK de Windows para obtener más información.

   Además, si selecciona **compatible con automatización**, a continuación, todos los parámetros de todos los métodos en el control deben ser variantes compatible.

### <a name="support"></a>Compatibilidad

Los conjuntos adicional admiten vario para el control.

- **Puntos de conexión**: permite a los puntos de conexión para el objeto mediante la realización de derivar de la clase del objeto [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) y permitir que exponga una interfaz de origen.

- **Licencia**: agrega compatibilidad para el control [licencias](/windows/desktop/com/licensing). Solo se pueden hospedar controles con licencia, si el equipo cliente tiene la licencia correcta.

## <a name="see-also"></a>Vea también

[Asistente para controles ATL](../../atl/reference/atl-control-wizard.md)

