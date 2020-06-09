---
title: Automation
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers, about Automation servers
- clients, Automation
- programmatic control [MFC]
- properties [MFC], Automation
- MFC, COM support
- OLE Automation
- Automation
- servers [MFC], Automation
- Automation clients
- sample applications [MFC], Automation
- methods [MFC]
- passing parameters, Automation
- Automation method [MFC]
- Automation, passing parameters
- Automation property [MFC]
- MFC COM, Automation
- methods [MFC], Automation
ms.assetid: 329117f0-c1aa-4680-a901-bfb71277dfba
ms.openlocfilehash: e5790be14f26f59c2b51b339c8bee7c5eca7d692
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616511"
---
# <a name="automation"></a>Automation

La automatización (antes conocida como automatización OLE) permite que una aplicación manipule objetos implementados en otra aplicación o exponga objetos para que se puedan manipular.

Un [servidor de automatización](automation-servers.md) es una aplicación (un tipo de servidor COM) que expone su funcionalidad a través de interfaces COM a otras aplicaciones, denominadas [clientes de automatización](automation-clients.md). La exposición permite a los clientes de automatización automatizar determinadas funciones al acceder a objetos directamente y usar los servicios que proporcionan.

Los servidores y clientes de automatización usan interfaces COM que se derivan siempre de `IDispatch` y toman y devuelven un conjunto específico de tipos de datos denominados tipos de automatización. Puede automatizar cualquier objeto que exponga una interfaz de automatización, con lo que proporciona métodos y propiedades a los que puede acceder desde otras aplicaciones. La automatización está disponible para objetos COM y OLE. El objeto automatizado puede ser local o remoto (en otra máquina accesible a través de una red); por lo tanto, hay dos categorías de automatización:

- Automatización (local).

- Automatización remota (a través de una red, mediante COM distribuido, o DCOM).

La exposición de objetos es beneficiosa si las aplicaciones proporcionan funcionalidad útil para otras aplicaciones. Por ejemplo, un control ActiveX es un tipo de servidor de automatización; la aplicación que hospeda el control ActiveX es el cliente de automatización de ese control.

Como otro ejemplo, un procesador de textos podría exponer su funcionalidad de revisión ortográfica a otros programas. La exposición de objetos permite a los proveedores mejorar sus aplicaciones mediante la funcionalidad lista para usar de otras aplicaciones. De esta manera, la automatización aplica algunos de los principios de la programación orientada a objetos, como la reusabilidad y la encapsulación, en el nivel de las propias aplicaciones.

Más importante es la compatibilidad que la automatización proporciona a los usuarios y a los proveedores de soluciones. Al exponer la funcionalidad de la aplicación mediante una interfaz común bien definida, la automatización permite generar soluciones completas en un único lenguaje de programación general, como Microsoft Visual Basic, en lugar de en lenguajes distintos de macro específicos de la aplicación.

Muchas aplicaciones comerciales, como Microsoft Excel y Microsoft Visual C++, permiten automatizar gran parte de su funcionalidad. Por ejemplo, en Visual C++, puede escribir macros de VBScript para automatizar compilaciones, aspectos de edición de código o tareas de depuración.

## <a name="passing-parameters-in-automation"></a><a name="_core_passing_parameters_in_automation"></a> Pasar parámetros en la automatización

Una dificultad a la hora de crear métodos de automatización es ayudar a proporcionar un mecanismo uniforme "seguro" para pasar datos entre clientes y servidores de automatización. La automatización usa el tipo **VARIANT** para pasar datos. El tipo **VARIANT** es una unión etiquetada. Tiene un miembro de datos para el valor (es decir, una unión anónima C++) y un miembro de datos que indica el tipo de información almacenada en la unión. El tipo **VARIANT** admite varios tipos de datos estándar: enteros de 2 y 4 bytes, números de punto flotante de 4 y 8 bytes, cadenas y valores booleanos. Además, admite los tipos **HRESULT** (códigos de error OLE), **Currency** (un tipo numérico de punto fijo) y **Date** (fecha y hora absolutas), así como punteros a `IUnknown` `IDispatch` interfaces e.

El tipo **VARIANT** se encapsula en la clase [COleVariant](reference/colevariant-class.md) . Las clases auxiliares **CURRENCY** y **DATE** están encapsuladas en las clases [COleCurrency](reference/colecurrency-class.md) y [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) .

## <a name="automation-samples"></a>Ejemplos de automatización

- [AUTOCLIK](../overview/visual-cpp-samples.md) Use este ejemplo para aprender técnicas de automatización y como base para aprender sobre automatización remota.

- [ACDUAL](../overview/visual-cpp-samples.md) Agrega interfaces duales a una aplicación de servidor de automatización.

- [CALCDRIV](../overview/visual-cpp-samples.md) Aplicación de cliente de automatización que controla MFCCALC.

- [INPROC](../overview/visual-cpp-samples.md) Ilustra una aplicación de servidor de automatización en proceso.

- [IPDRIVE](../overview/visual-cpp-samples.md) Aplicación de cliente de automatización que controla INPROC.

- [MFCCALC](../overview/visual-cpp-samples.md) Muestra una aplicación de cliente de automatización.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Clientes de automatización](automation-clients.md)

- [Servidores de automatización](automation-servers.md)

- [OLE](ole-in-mfc.md)

- [tecnología activa](mfc-com.md)

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Agregar una clase de automatización](automation-servers.md)

- [Usar bibliotecas de tipos](automation-clients-using-type-libraries.md)

- [Acceder a servidores de automatización](automation-servers.md)

- [Escribir clientes de automatización en C++](automation-clients.md)

## <a name="see-also"></a>Consulte también

[MFC COM](mfc-com.md)
