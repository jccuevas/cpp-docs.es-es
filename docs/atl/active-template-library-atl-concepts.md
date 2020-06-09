---
title: Conceptos de Active Template Library (ATL)
ms.date: 05/06/2019
helpviewer_keywords:
- ATL, about ATL
ms.assetid: a3960991-4d76-4da5-9568-3fa7fde53ff4
ms.openlocfilehash: cc96b5ed931713ca64a0582ca1cc18a8526ea8af
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616681"
---
# <a name="active-template-library-atl-concepts"></a>Conceptos de Active Template Library (ATL)

Active Template Library (ATL) es un conjunto de clases de C++ basadas en plantillas que permiten crear objetos COM (Modelo de objetos componentes) pequeños y rápidos. Ofrece compatibilidad especial con algunas características esenciales de COM, como las implementaciones estándar, las interfaces duales, las interfaces de enumerador COM estándar, los puntos de conexión, las interfaces divisibles y los controles ActiveX.

Si hace mucha programación de ATL, le interesa saber más sobre los atributos de COM y .NET, que está diseñados para simplificar la programación de COM. Para más información, vea [Atributos de C++ para COM y .NET](../windows/attributed-programming-concepts.md). (No deben confundirse los atributos de COM y .NET con la característica \[\[attribute]] en C++ estándar).

## <a name="in-this-section"></a>En esta sección

[Introducción a COM y ATL](introduction-to-com-and-atl.md)<br/>
Presenta los conceptos principales detrás del Modelo de objetos componentes (COM). En este artículo también se explica brevemente qué es ATL y cuándo se debe usar.

[Aspectos básicos de los objetos COM de ATL](fundamentals-of-atl-com-objects.md)<br/>
Describe la relación entre diversas clases ATL y cómo se implementan esas clases.

[Interfaces duales y ATL](dual-interfaces-and-atl.md)<br/>
Describe las interfaces duales desde una perspectiva de ATL.

[Colecciones y enumeradores de ATL](atl-collections-and-enumerators.md)<br/>
Describe la creación y la implementación de colecciones y enumeradores de ATL.

[Fundamentos de controles compuestos](atl-composite-control-fundamentals.md)<br/>
Proporciona instrucciones paso a paso para crear un control compuesto. Un control compuesto es un tipo de control ActiveX que puede contener otros controles ActiveX o controles de Windows.

[Preguntas más frecuentes sobre contención de controles ATL](atl-control-containment-faq.md)<br/>
Se tratan cuestiones fundamentales relacionadas con el hospedaje de controles con ATL.

[Páginas de propiedades COM de ATL](atl-com-property-pages.md)<br/>
Muestra cómo especificar e implementar páginas de propiedades COM.

[Compatibilidad de ATL con controles DHTML](atl-support-for-dhtml-controls.md)<br/>
Proporciona instrucciones paso a paso para serializar un objeto.

[Puntos de conexión ATL](atl-connection-points.md)<br/>
Explica qué son los puntos de conexión y cómo los implementa ATL.

[Control de eventos en ATL](event-handling-and-atl.md)<br/>
Se describen los pasos que debe realizar para controlar eventos COM mediante clases [IDispEventImpl](reference/idispeventimpl-class.md) y [IDispEventSimpleImpl](reference/idispeventsimpleimpl-class.md) de ATL.

[ATL y el contador de referencias de subprocesamiento libre](atl-and-the-free-threaded-marshaler.md)<br/>
Proporciona detalles sobre la opción Asistente para objetos simples ATL que permite que la clase agregue el contador de referencias de subprocesamiento libre (FTM).

[Especificar el modelo de subprocesos del proyecto](specifying-the-threading-model-for-a-project-atl.md)<br/>
Describe las macros que están disponibles para controlar el rendimiento en tiempo de ejecución relacionado con los subprocesos del proyecto.

[Clases de módulo de ATL](atl-module-classes.md)<br/>
Describe las nuevas clases de módulo de ATL 7.0. Las clases de módulo implementan las funciones básicas necesarias para ATL.

[Servicios ATL](atl-services.md)<br/>
Trata la serie de eventos que se producen cuando se implementa un servicio. También habla de algunos de los conceptos relacionados con el desarrollo de un servicio.

[Clases de ventana ATL](atl-window-classes.md)<br/>
Describe cómo crear clases, superclases y subclases de ventanas en ATL. Las clases de ventanas de ATL no son clases COM.

[Clases de colección de ATL](atl-collection-classes.md)<br/>
Describe cómo usar matrices y mapas en ATL.

[Componente del Registro de ATL (Registrador)](atl-registry-component-registrar.md)<br/>
Describe la sintaxis de scripting de ATL y los parámetros reemplazables. También explica cómo configurar un vínculo estático al registrador.

[Programar con ATL y código en tiempo de ejecución de C](programming-with-atl-and-c-run-time-code.md)<br/>
Describe las ventajas de vincular estática o dinámicamente a la biblioteca en tiempo de ejecución de C (CRT).

[Programar con CComBSTR](programming-with-ccombstr-atl.md)<br/>
Describe varias situaciones con las que hay que tener cuidado al programar con `CComBSTR`.

[Referencia de codificación](atl-encoding-reference.md)<br/>
Proporciona funciones y macros que admiten la codificación en una variedad de estándares comunes de Internet, como uuencode, hexadecimal y UTF8 en atlenc.h.

[Referencia de utilidades](atl-utilities-reference.md)<br/>
Proporciona código para manipular las rutas de acceso y direcciones URL en forma de [CPathT](reference/cpatht-class.md) y [CUrl](reference/curl-class.md). Puede usar un grupo de subprocesos, [CThreadPool](reference/cthreadpool-class.md), en sus propias aplicaciones. Este código puede encontrarse en atlutil.h y atlutil.h.

## <a name="related-sections"></a>Secciones relacionadas

[Tutorial de ATL](active-template-library-atl-tutorial.md)<br/>
Explica el proceso de creación de un control y muestra algunos conceptos básicos de ATL en el proceso.

[Ejemplos de ATL](../overview/visual-cpp-samples.md)<br/>
Proporciona descripciones y vínculos a los programas de ejemplo de ATL.

[Creación de un proyecto ATL](reference/creating-an-atl-project.md)<br/>
Contiene información sobre el Asistente para proyectos ATL.

[Asistente para controles ATL](reference/atl-control-wizard.md)<br/>
Describe cómo agregar clases.

[Programación con atributos](../windows/attributed-programming-concepts.md)<br/>
Proporciona información general sobre el uso de atributos para simplificar la programación de COM, además de una lista de vínculos a temas más detallados.

[Información general de la clase ATL](atl-class-overview.md)<br/>
Proporciona información de referencia y vínculos a las clases ATL.
