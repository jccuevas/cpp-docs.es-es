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
ms.openlocfilehash: 25c98c3683a8656bb5188f22d0464d25a4901f49
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364528"
---
# <a name="ole-background-mfc-implementation"></a>Nociones de OLE: Implementación de MFC

Debido al tamaño y la complejidad de la API OLE sin procesar, llamarla directamente para escribir aplicaciones OLE puede llevar mucho tiempo. El objetivo de la implementación de OLE de la biblioteca microsoft Foundation Class es reducir la cantidad de trabajo que tiene que hacer para escribir aplicaciones con todas las funciones compatibles con OLE.

En este artículo se explican las partes de la API OLE que no se han implementado dentro de MFC. En la discusión también se explica cómo se asigna lo que se implementa a la sección OLE del Windows SDK.

## <a name="portions-of-ole-not-implemented-by-the-class-library"></a><a name="_core_portions_of_ole_not_implemented_by_the_class_library"></a>Partes de OLE no implementadas por la biblioteca de clases

MFC no proporciona directamente algunas interfaces y características de OLE. Si desea usar estas características, puede llamar a la API OLE directamente.

Interfaz IMoniker La `IMoniker` interfaz se implementa mediante `COleServerItem` la biblioteca de clases (por ejemplo, la clase) pero no se ha expuesto previamente al programador. Para obtener más información acerca de esta interfaz, vea implementaciones de OLE Moniker en la sección OLE del Windows SDK. Sin embargo, vea también la clase [CMonikerFile](../mfc/reference/cmonikerfile-class.md) y [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md).

Interfaces IUnknown e `IUnknown` IMarshal La interfaz se implementa en la biblioteca de clases, pero no se expone al programador. La `IMarshal` biblioteca de clases no implementa la interfaz, pero se utiliza internamente. Los servidores de automatización creados con la biblioteca de clases ya tienen capacidades de cálculo de referencias integradas.

Los archivos compuestos de Docfiles (archivos compuestos) son parcialmente compatibles con la biblioteca de clases. No se admite ninguna de las funciones que manipulan directamente archivos compuestos más allá de la creación. MFC usa `COleFileStream` la clase para admitir la manipulación de secuencias con funciones de archivo estándar. Para obtener más información, consulte el artículo [Contenedores: Archivos compuestos](../mfc/containers-compound-files.md).

Servidores en proceso y controladores de objetos Los servidores en proceso y los controladores de objetos permiten la implementación de datos de edición visual o objetos completos del modelo de objetos componentes (COM) en una biblioteca de vínculos dinámicos (DLL). Para ello, puede implementar el archivo DLL llamando a la API OLE directamente. Sin embargo, si está escribiendo un servidor de automatización y el servidor no tiene interfaz de usuario, puede usar AppWizard para convertir el servidor en un servidor en proceso y ponerlo completamente en un archivo DLL. Para obtener más información acerca de estos temas, vea [Servidores de automatización](../mfc/automation-servers.md).

> [!TIP]
> La forma más fácil de implementar un servidor de automation es colocarlo en un archivo DLL. MFC admite este enfoque.

Para obtener más información sobre cómo las clases OLE de Microsoft Foundation implementan interfaces OLE, vea Notas técnicas de MFC [38](../mfc/tn038-mfc-ole-iunknown-implementation.md), [39](../mfc/tn039-mfc-ole-automation-implementation.md)y [40](../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md).

## <a name="see-also"></a>Consulte también

[Nociones de OLE](../mfc/ole-background.md)<br/>
[Nociones de OLE: Estrategias de implementación](../mfc/ole-background-implementation-strategies.md)
