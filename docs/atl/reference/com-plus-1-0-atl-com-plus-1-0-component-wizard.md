---
title: COM+ 1.0, Asistente para componentes ATL COM+ 1.0
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.mts.options
ms.assetid: 2fbe259c-6be1-4d0e-9cfe-721c75c97cb1
ms.openlocfilehash: bff7f87fbdebbff9a1823ae8718c64be4f47a2ea
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707456"
---
# <a name="com-10-atl-com-10-component-wizard"></a>COM+ 1.0, Asistente para componentes ATL COM+ 1.0

::: moniker range="vs-2019"

Este asistente no está disponible en Visual Studio 2019 ni en versiones posteriores.

::: moniker-end

::: moniker range="<=vs-2017"

Use esta página del Asistente para componentes COM+ 1.0 ATL para especificar el tipo de interfaz y las interfaces adicionales que se deben admitir.

Para obtener más información sobre los proyectos ATL y las clases COM de ATL, vea [Componentes de escritorio COM de ATL](../../atl/atl-com-desktop-components.md).

- **Interface**

   Indica el tipo de interfaz que admite el objeto. De forma predeterminada, el objeto admite una interfaz dual.

   |Opción|Descripción|
   |------------|-----------------|
   |**Dual**|Especifica que el objeto admite una interfaz dual (su tabla virtual tiene funciones de interfaz personalizadas y métodos `IDispatch` de enlace en tiempo de ejecución). Permite que los clientes COM y los controladores de automatización accedan al objeto.|
   |**Custom**|Especifica que el objeto admite una interfaz personalizada (su tabla virtual tiene funciones de interfaz personalizadas). Una interfaz personalizada puede ser más rápida que una interfaz dual, especialmente entre los límites de procesos.<br /><br /> - **Compatible con automatización** Agrega compatibilidad con la automatización a la interfaz personalizada. Para los proyectos con atributos, establece el atributo **oleautomation** en la coclase.|

- **Con colas**

   Indica que los clientes pueden llamar a este componente de forma asincrónica mediante colas de mensajes. Agrega la macro con atributos de componente custom(TLBATTR_QUEUEABLE, 0) al archivo .h (en proyectos con atributos) o al archivo .idl (en proyectos sin atributos).

- **Compatibilidad**

   Indica compatibilidad adicional para el control de errores y objetos.

   |Opción|Descripción|
   |------------|-----------------|
   |**ISupportErrorInfo**|Crea compatibilidad con la interfaz [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) para que el objeto pueda devolver información de error al cliente.|
   |**IObjectControl**|Proporciona al objeto acceso a los tres métodos [IObjectControl](/windows/desktop/api/comsvcs/nn-comsvcs-iobjectcontrol): [Activate](/windows/desktop/api/comsvcs/nf-comsvcs-iobjectcontrol-activate), [CanBePooled](/windows/desktop/api/comsvcs/nf-comsvcs-iobjectcontrol-canbepooled) y [Deactivate](/windows/desktop/api/comsvcs/nf-comsvcs-iobjectcontrol-deactivate).|
   |**IObjectConstruct**|Crea compatibilidad con la interfaz [IObjectConstruct](/windows/desktop/api/comsvcs/nn-comsvcs-iobjectconstruct) para administrar la transferencia de parámetros desde otros métodos u objetos.|

- **Transacción**

   Indica que el objeto admite transacciones. Incluye el archivo mtxattr.h en el archivo .idl (en proyectos sin atributos).

   |Opción|Descripción|
   |------------|-----------------|
   |**Compatible**|Especifica que el objeto nunca es la raíz de un flujo de transacciones mediante la adición de la macro de atributos de componente custom(TLBATTR_TRANS_SUPPORTED,0) al archivo .h (en proyectos con atributos) o al archivo .idl (en proyectos sin atributos).|
   |**Obligatoria**|Especifica que el objeto puede ser o no la raíz de un flujo de transacciones mediante la adición de la macro de atributos de componente custom(TLBATTR_TRANS_REQUIRED,0) al archivo .h (en proyectos con atributos) o al archivo .idl (en proyectos sin atributos).|
   |**No se admite**|Especifica que el objeto excluye las transacciones. Agrega la macro con atributos de componente custom(TLBATTR_TRANS_NOTSUPP,0) al archivo .h (en proyectos con atributos) o al archivo .idl (en proyectos sin atributos).|
   |**Necesita nueva**|Especifica que el objeto siempre es la raíz de un flujo de transacciones mediante la adición de la macro de atributos de componente custom(TLBATTR_TRANS_REQNEW,0) al archivo .h (en proyectos con atributos) o al archivo .idl (en proyectos sin atributos).|

::: moniker-end

## <a name="see-also"></a>Vea también

[Asistente para componentes ATL COM+ 1.0](../../atl/reference/atl-com-plus-1-0-component-wizard.md)<br/>
[Componente COM+ 1.0 ATL](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)
