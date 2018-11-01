---
title: COM+ 1.0, Asistente para componentes ATL COM+ 1.0
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.mts.options
ms.assetid: 2fbe259c-6be1-4d0e-9cfe-721c75c97cb1
ms.openlocfilehash: 014193f4017aa47b819558cbd4753e6abcffcaaf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562063"
---
# <a name="com-10-atl-com-10-component-wizard"></a>COM+ 1.0, Asistente para componentes ATL COM+ 1.0

Use esta página del Asistente para componentes ATL COM + 1.0 para especificar el tipo de interfaz y las interfaces adicionales que se deben admitir.

Para obtener más información sobre los proyectos ATL y clases COM de ATL, vea [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md).

- **Interface**

   Indica el tipo de interfaz es compatible con el objeto. De forma predeterminada, el objeto admite una interfaz dual.

   |Opción|Descripción|
   |------------|-----------------|
   |**Dual**|Especifica que el objeto admite una interfaz dual (su tabla vtable tiene funciones de interfaz personalizada y un enlace `IDispatch` métodos). Permite que los clientes COM y los controladores de automatización tener acceso al objeto.|
   |**Custom**|Especifica que el objeto admite una interfaz personalizada (su tabla vtable tiene funciones de interfaz personalizada). Una interfaz personalizada puede ser más rápida que una interfaz dual, especialmente entre los límites del proceso.<br /><br /> - **Compatible con automatización** agrega compatibilidad con automatización a la interfaz personalizada. Para proyectos con atributos, Establece el **oleautomation** atributo en la coclase.|

- **Uno de estos**

   Indica que los clientes pueden llamar a este componente de forma asincrónica utilizando colas de mensajes. Agrega atribuida de componente macro personalizado (TLBATTR_QUEUEABLE, 0) al archivo .h (proyectos con atributos) o al archivo .idl (proyectos sin atributos).

- **Soporte técnico**

   Indica compatibilidad adicional para el control de control y objeto de error.

   |Opción|Descripción|
   |------------|-----------------|
   |**ISupportErrorInfo**|Crea la compatibilidad con la [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) interfaz para que el objeto puede devolver información de error al cliente.|
   |**IObjectControl**|Proporciona el acceso a los objetos a los tres [IObjectControl](/windows/desktop/api/comsvcs/nn-comsvcs-iobjectcontrol) métodos: [activar](/windows/desktop/api/comsvcs/nf-comsvcs-iobjectcontrol-activate), [CanBePooled](/windows/desktop/api/comsvcs/nf-comsvcs-iobjectcontrol-canbepooled), y [Deactivate](/windows/desktop/api/comsvcs/nf-comsvcs-iobjectcontrol-deactivate).|
   |**IObjectConstruct**|Crea la compatibilidad con la [IObjectConstruct](/windows/desktop/api/comsvcs/nn-comsvcs-iobjectconstruct) interfaz para administrar pasar parámetros desde otros métodos u objetos.|

- **Transacción**

   Indica que el objeto admite transacciones. Incluye el archivo mtxattr.h en el archivo .idl (proyectos sin atributos).

   |Opción|Descripción|
   |------------|-----------------|
   |**Compatible**|Especifica que el objeto nunca es la raíz de una secuencia de transacción agregando el custom(TLBATTR_TRANS_SUPPORTED,0) de macro de atributo de componente al archivo .h (proyectos con atributos) o al archivo .idl (proyectos sin atributos).|
   |**Obligatoria**|Especifica que el objeto puede o no sea la raíz de una secuencia de transacción agregando el custom(TLBATTR_TRANS_REQUIRED,0) de macro de atributo de componente al archivo .h (proyectos con atributos) o al archivo .idl (proyectos sin atributos).|
   |**No se admite**|Especifica que el objeto excluye las transacciones. Agrega el custom(TLBATTR_TRANS_NOTSUPP,0) de macro de atributo de componente al archivo .h (proyectos con atributos) o al archivo .idl (proyectos sin atributos).|
   |**Se requiere nueva**|Especifica que el objeto siempre es la raíz de una secuencia de transacción agregando el custom(TLBATTR_TRANS_REQNEW,0) de macro de atributo de componente al archivo .h (proyectos con atributos) o al archivo .idl (proyectos sin atributos).|

## <a name="see-also"></a>Vea también

[Asistente para componentes ATL COM+ 1.0](../../atl/reference/atl-com-plus-1-0-component-wizard.md)<br/>
[Componente COM + 1.0 ATL](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)

