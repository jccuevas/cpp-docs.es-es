---
title: Fundamentos de los objetos COM de ATL
ms.date: 11/19/2018
helpviewer_keywords:
- COM, and ATL
- ATL, COM
- ATL COM objects
- COM objects, ATL
ms.assetid: 0f9c9d98-cc28-45da-89ac-dc94cee422fe
ms.openlocfilehash: 651413534ed44143e2a0fdaf00bdabd6e5d57010
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319558"
---
# <a name="fundamentals-of-atl-com-objects"></a>Fundamentos de los objetos COM de ATL

En la ilustración siguiente se muestra la relación entre las clases e interfaces que se utilizan para definir un objeto COM ATL.

![Estructura ATL](../atl/media/vc307y1.gif "Estructura ATL")

> [!NOTE]
> Este diagrama `CComObject` muestra que `CYourClass` se `CComAggObject` deriva `CComPolyObject` `CYourClass` de mientras que incluyen como una variable miembro.

Hay tres maneras de definir un objeto COM ATL. La opción estándar es `CComObject` utilizar la clase `CYourClass`que se deriva de . La segunda opción es crear un objeto `CComAggObject` agregado mediante la clase. La tercera opción es `CComPolyObject` utilizar la clase. `CComPolyObject`actúa como un híbrido: puede `CComObject` funcionar como `CComAggObject` una clase o como una clase, dependiendo de cómo se crea por primera vez. Para obtener más información `CComPolyObject` sobre cómo utilizar la clase, vea [CComPolyObject (Clase).](../atl/reference/ccompolyobject-class.md)

Cuando se utiliza ATL COM estándar, se utilizan dos objetos: un objeto externo y un objeto interno. Los clientes externos tienen acceso a la funcionalidad del objeto interno a través de las funciones contenedoras que se definen en el objeto externo. El objeto externo `CComObject`es de tipo .

Cuando se utiliza un objeto agregado, el objeto externo no proporciona contenedores para la funcionalidad del objeto interno. En su lugar, el objeto externo proporciona un puntero al que tienen acceso directamente los clientes externos. En este escenario, el objeto `CComAggObject`externo es de tipo . El objeto interno es una variable miembro del objeto `CYourClass`externo y es de tipo .

Dado que el cliente no tiene que pasar por el objeto externo para interactuar con el objeto interno, los objetos agregados suelen ser más eficaces. Además, el objeto externo no tiene que conocer la funcionalidad del objeto agregado, dado que la interfaz del objeto agregado está directamente disponible para el cliente. Sin embargo, no todos los objetos se pueden agregar. Para que un objeto se agregue, debe diseñarse teniendo en cuenta la agregación.

ATL implementa [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) en dos fases:

- [CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md)o [CComPolyObject](../atl/reference/ccompolyobject-class.md) implementa los `IUnknown` métodos.

- [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) administra el recuento `IUnknown`de referencias y los punteros externos de .

Otras clases controlan otros aspectos del objeto COM DE ATL:

- [CComCoClass](../atl/reference/ccomcoclass-class.md) define el generador de clases predeterminado del objeto y el modelo de agregación.

- [IDispatchImpl](../atl/reference/idispatchimpl-class.md) proporciona una implementación predeterminada de la `IDispatch Interface` parte de cualquier interfaz dual en el objeto.

- [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) implementa `ISupportErrorInfo` la interfaz que garantiza que la información de error se puede propagar correctamente por la cadena de llamadas.

## <a name="in-this-section"></a>En esta sección

[Implementar CComObjectRootEx](../atl/implementing-ccomobjectrootex.md)<br/>
Mostrar entradas de mapa `CComObjectRootEx`COM de ejemplo para implementar .

[Implementar CComObject, CComAggObject y CComPolyObject](../atl/implementing-ccomobject-ccomaggobject-and-ccompolyobject.md)<br/>
Describe cómo afectan las macros de `CComObject` `CComAggObject`_AGGREGATABLE `CComPolyObject` **DECLARE_\*** al uso de , , y .

[Admitir IDispatch e IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md)<br/>
Enumera las clases de implementación `IDispatch` ATL que se usarán para admitir las `IErrorInfo` interfaces.

[Admitir IDispEventImpl](../atl/supporting-idispeventimpl.md)<br/>
Describe los pasos para implementar un punto de conexión para la clase.

[Cambio del modelo predeterminado de generador de clases y agregación](../atl/changing-the-default-class-factory-and-aggregation-model.md)<br/>
Mostrar qué macros utilizar para cambiar el generador de clases predeterminado y el modelo de agregación.

[Creación de un objeto agregado](../atl/creating-an-aggregated-object.md)<br/>
Enumera los pasos para crear un objeto agregado.

## <a name="related-sections"></a>Secciones relacionadas

[Creación de un proyecto ATL](../atl/reference/creating-an-atl-project.md)<br/>
Proporciona información sobre cómo crear un objeto COM ATL.

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Proporciona vínculos a temas sobre cómo programar utilizando Active Template Library.

## <a name="see-also"></a>Consulte también

[Conceptos](../atl/active-template-library-atl-concepts.md)
