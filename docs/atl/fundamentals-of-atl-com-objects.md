---
title: Aspectos básicos de los objetos COM de ATL
ms.date: 11/19/2018
helpviewer_keywords:
- COM, and ATL
- ATL, COM
- ATL COM objects
- COM objects, ATL
ms.assetid: 0f9c9d98-cc28-45da-89ac-dc94cee422fe
ms.openlocfilehash: ec83539b2d7101c534bbc1df33577df422e76152
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492365"
---
# <a name="fundamentals-of-atl-com-objects"></a>Aspectos básicos de los objetos COM de ATL

En la ilustración siguiente se muestra la relación entre las clases e interfaces que se utilizan para definir un objeto COM ATL.

![Estructura ATL](../atl/media/vc307y1.gif "Estructura ATL")

> [!NOTE]
>  `CComObject` `CYourClass` `CComPolyObject` Eneste`CYourClass` diagrama se muestra que se deriva de yqueseincluyecomounavariablemiembro.`CComAggObject`

Hay tres maneras de definir un objeto COM ATL. La opción estándar es usar la `CComObject` clase que se deriva de. `CYourClass` La segunda opción consiste en crear un objeto agregado mediante la `CComAggObject` clase. La tercera opción es usar la `CComPolyObject` clase. `CComPolyObject`actúa como un híbrido: puede funcionar como una `CComObject` clase o `CComAggObject` como una clase, en función de cómo se cree por primera vez. Para obtener más información sobre cómo usar la `CComPolyObject` clase, vea [CComPolyObject (clase](../atl/reference/ccompolyobject-class.md)).

Cuando se usa el estándar ATL COM, se usan dos objetos: un objeto externo y un objeto interno. Los clientes externos tienen acceso a la funcionalidad del objeto interno a través de las funciones de contenedor definidas en el objeto externo. El objeto externo es de tipo `CComObject`.

Cuando se usa un objeto agregado, el objeto externo no proporciona contenedores para la funcionalidad del objeto interno. En su lugar, el objeto externo proporciona un puntero al que tienen acceso directamente los clientes externos. En este escenario, el objeto externo es de tipo `CComAggObject`. El objeto interno es una variable miembro del objeto externo y es de tipo `CYourClass`.

Dado que el cliente no tiene que pasar por el objeto externo para interactuar con el objeto interno, los objetos agregados suelen ser más eficaces. Además, el objeto externo no tiene que conocer la funcionalidad del objeto agregado, dado que la interfaz del objeto agregado está directamente disponible para el cliente. Sin embargo, no se pueden agregar todos los objetos. Para que un objeto se agregue, debe diseñarse con la agregación en mente.

ATL implementa [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) en dos fases:

- [CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md)o [CComPolyObject](../atl/reference/ccompolyobject-class.md) implementa los `IUnknown` métodos.

- [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) administra el recuento de referencias y los punteros externos de `IUnknown`.

Otras clases controlan otros aspectos del objeto COM ATL:

- [CComCoClass](../atl/reference/ccomcoclass-class.md) define el generador de clases predeterminado del objeto y el modelo de agregación.

- [IDispatchImpl](../atl/reference/idispatchimpl-class.md) proporciona una implementación predeterminada de la `IDispatch Interface` parte de cualquier interfaz dual en el objeto.

- [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) implementa la `ISupportErrorInfo` interfaz que garantiza que la información de error se puede propagar correctamente hacia arriba en la cadena de llamadas.

## <a name="in-this-section"></a>En esta sección

[Implementar CComObjectRootEx](../atl/implementing-ccomobjectrootex.md)<br/>
Mostrar entradas de mapa COM de ejemplo `CComObjectRootEx`para implementar.

[Implementar CComObject, CComAggObject y CComPolyObject](../atl/implementing-ccomobject-ccomaggobject-and-ccompolyobject.md)<br/>
Describe cómo las macros de **DECLARE_\*_AGGREGATABLE** afectan al uso de `CComObject`, `CComAggObject`y `CComPolyObject`.

[Admitir IDispatch e IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md)<br/>
Enumera las clases de implementación de ATL que se usarán `IErrorInfo` para admitir las `IDispatch` interfaces y.

[Admitir IDispEventImpl](../atl/supporting-idispeventimpl.md)<br/>
Describe los pasos necesarios para implementar un punto de conexión para la clase.

[Cambiar el generador de clases predeterminado y el modelo de agregación](../atl/changing-the-default-class-factory-and-aggregation-model.md)<br/>
Mostrar las macros que se van a usar para cambiar el generador de clases predeterminado y el modelo de agregación.

[Crear un objeto agregado](../atl/creating-an-aggregated-object.md)<br/>
Enumera los pasos para crear un objeto agregado.

## <a name="related-sections"></a>Secciones relacionadas

[Creación de un proyecto ATL](../atl/reference/creating-an-atl-project.md)<br/>
Proporciona información sobre la creación de un objeto COM ATL.

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Proporciona vínculos a temas sobre cómo programar utilizando Active Template Library.

## <a name="see-also"></a>Vea también

[Conceptos](../atl/active-template-library-atl-concepts.md)
