---
title: 'Nociones de OLE: Implementación de MFC'
ms.date: 11/04/2016
f1_keywords:
- IMarshall
- IMoniker
helpviewer_keywords:
- MFC libraries, implementing
- OLE MFC library implementation
- OLE IMarshal interface
- IMoniker interface, MFC
- IMarshall class [MFC]
- OLE, compound files
- OLE IMoniker interface
- OLE IUnknown
ms.assetid: 2b67016a-d78e-4d60-925f-c28ec8fb6180
ms.openlocfilehash: 1dffdafbd02697db5aec341fec253c84217a0faf
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619873"
---
# <a name="ole-background-mfc-implementation"></a>Nociones de OLE: Implementación de MFC

Debido al tamaño y la complejidad de la API de OLE sin formato, la llamada directa a la escritura de aplicaciones OLE puede llevar mucho tiempo. El objetivo de la implementación de biblioteca MFC de OLE es reducir la cantidad de trabajo que tiene que hacer para escribir aplicaciones compatibles con OLE y completas.

En este artículo se explican las partes de la API OLE que no se han implementado en MFC. La explicación también explica cómo se implementan las asignaciones en la sección OLE del Windows SDK.

## <a name="portions-of-ole-not-implemented-by-the-class-library"></a><a name="_core_portions_of_ole_not_implemented_by_the_class_library"></a>Partes de OLE no implementadas por la biblioteca de clases

MFC no proporciona directamente algunas interfaces y características de OLE. Si desea utilizar estas características, puede llamar a la API OLE directamente.

Interfaz IMoniker la `IMoniker` interfaz la implementa la biblioteca de clases (por ejemplo, la `COleServerItem` clase), pero no se ha expuesto previamente al programador. Para obtener más información sobre esta interfaz, consulte implementaciones de moniker OLE en la sección OLE del Windows SDK. Sin embargo, vea también la clase [CMonikerFile](reference/cmonikerfile-class.md) y [CAsyncMonikerFile](reference/casyncmonikerfile-class.md).

Interfaces IUnknown e IMarshal la `IUnknown` interfaz se implementa mediante la biblioteca de clases, pero no se expone al programador. La `IMarshal` biblioteca de clases no implementa la interfaz, pero se usa internamente. Los servidores de automatización compilados con la biblioteca de clases ya tienen capacidades de serialización integradas.

Los archivos compuestos de Docfiles (archivos compuestos) se admiten parcialmente en la biblioteca de clases. No se admite ninguna de las funciones que manipulan directamente los archivos compuestos más allá de la creación. MFC utiliza la clase `COleFileStream` para admitir la manipulación de secuencias con funciones de archivo estándar. Para obtener más información, vea el artículo [contenedores: archivos compuestos](containers-compound-files.md).

Los servidores en proceso y los controladores de objetos en proceso y los controladores de objetos permiten la implementación de datos de edición visual o de objetos de modelo de objetos componentes (COM) completos en una biblioteca de vínculos dinámicos (DLL). Para ello, puede implementar el archivo DLL llamando directamente a la API de OLE. Sin embargo, si está escribiendo un servidor de automatización y el servidor no tiene ninguna interfaz de usuario, puede usar AppWizard para convertir el servidor en un servidor en proceso y colocarlo completamente en un archivo DLL. Para obtener más información acerca de estos temas, consulte [servidores de Automation](automation-servers.md).

> [!TIP]
> La forma más fácil de implementar un servidor de automatización es colocarlo en un archivo DLL. MFC admite este enfoque.

Para obtener más información sobre cómo las clases OLE de Microsoft Foundation implementan interfaces OLE, consulte las notas técnicas [38](tn038-mfc-ole-iunknown-implementation.md), [39](tn039-mfc-ole-automation-implementation.md)y [40](tn040-mfc-ole-in-place-resizing-and-zooming.md)de MFC.

## <a name="see-also"></a>Consulte también

[Nociones de OLE](ole-background.md)<br/>
[Nociones de OLE: Estrategias de implementación](ole-background-implementation-strategies.md)
