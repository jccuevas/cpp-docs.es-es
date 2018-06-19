---
title: Conceptos de Active Template Library (ATL) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, about ATL
ms.assetid: a3960991-4d76-4da5-9568-3fa7fde53ff4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5636f92df42116b838c24c21d81f0b320f7d69c1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358119"
---
# <a name="active-template-library-atl-concepts"></a>Conceptos de Active Template Library (ATL)
Active Template Library (ATL) es un conjunto de clases de C++ basadas en plantillas que le permiten crear objetos de modelo de objetos componentes (COM) pequeña y rápida. Ofrece una compatibilidad especial para las características COM clave, incluidas las implementaciones estándar, interfaces duales, las interfaces del enumerador COM estándares, puntos de conexión, interfaces divisibles y los controles ActiveX.  
  
 Si lo hace mucho de la programación de ATL, desea obtener más información acerca de los atributos, una característica nueva en Visual C++ .NET que está diseñado para simplificar la programación COM. Para obtener más información, consulte [programación con atributos](../windows/attributed-programming-concepts.md).  
  
## <a name="in-this-section"></a>En esta sección  
 [Tutorial ATL](../atl/active-template-library-atl-tutorial.md)  
 Le guiará por la creación de un control y enseña los fundamentos de ATL en el proceso.  
  
 [Introducción a COM y ATL](../atl/introduction-to-com-and-atl.md)  
 Presenta los conceptos principales detrás el modelo de objetos componentes (COM). Este artículo explica también brevemente qué es ATL y cuándo se debe utilizar.  
  
 [Aspectos básicos de los objetos ATL COM](../atl/fundamentals-of-atl-com-objects.md)  
 Describe la relación entre diversas clases ATL y cómo se implementan esas clases.  
  
 [Interfaces duales y ATL](../atl/dual-interfaces-and-atl.md)  
 Describe las interfaces duales desde la perspectiva de ATL.  
  
 [Colecciones y enumeradores de ATL](../atl/atl-collections-and-enumerators.md)  
 Describe la creación e implementación de colecciones y enumeradores de ATL.  
  
 [Fundamentos de controles compuestos](../atl/atl-composite-control-fundamentals.md)  
 Proporciona instrucciones paso a paso para crear un control compuesto. Un control compuesto es un tipo de control ActiveX que puede contener otros controles ActiveX o controles de Windows.  
  
 [Preguntas más frecuentes sobre contención de controles ATL](../atl/atl-control-containment-faq.md)  
 Trata cuestiones fundamentales relacionadas con el hospedaje de controles con ATL.  
  
 [Páginas de propiedades COM de ATL](../atl/atl-com-property-pages.md)  
 Muestra cómo especificar e implementar páginas de propiedades COM.  
  
 [Compatibilidad de ATL con controles DHTML](../atl/atl-support-for-dhtml-controls.md)  
 Proporciona instrucciones paso a paso para crear un control DHTML.  
  
 [Puntos de conexión en ATL](../atl/atl-connection-points.md)  
 Explica qué son los puntos de conexión y cómo los implementa la ATL.  
  
 [Control de eventos en ATL](../atl/event-handling-and-atl.md)  
 Describe los pasos que debe realizar para controlar eventos COM por medio de ATL [IDispEventImpl](../atl/reference/idispeventimpl-class.md) y [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) clases.  
  
 [ATL y el contador de referencias de subprocesamiento libre](../atl/atl-and-the-free-threaded-marshaler.md)  
 Proporciona información sobre la opción de ATL Simple objeto del asistente que permite a la clase agregar el contador de referencias de subprocesamiento libre (FTM).  
  
 [Especificar el modelo de subprocesamiento del proyecto](../atl/specifying-the-threading-model-for-a-project-atl.md)  
 Describe las macros que están disponibles para controlar el rendimiento del tiempo de ejecución relacionados con los subprocesos en el proyecto.  
  
 [Clases de módulo de ATL](../atl/atl-module-classes.md)  
 Describe las clases de módulo nuevas en ATL 7.0. Clases de módulo implementan la funcionalidad básica requerida por ATL.  
  
 [Servicios ATL](../atl/atl-services.md)  
 Trata la serie de eventos que se producen cuando se implementa un servicio. También explica algunos de los conceptos relacionados con el desarrollo de un servicio.  
  
 [Clases de ventana ATL](../atl/atl-window-classes.md)  
 Describe cómo crear, superclase y subclases de ventanas en ATL. Las clases de ventana ATL no son clases COM.  
  
 [Clases de colección de ATL](../atl/atl-collection-classes.md)  
 Describe cómo utilizar matrices y mapas en ATL.  
  
 [El componente de registro ATL (registrador)](../atl/atl-registry-component-registrar.md)  
 Describe ATL scripting sintaxis y los parámetros reemplazables. También se explica cómo configurar un vínculo estático al registrador.  
  
 [Programar con ATL y código en tiempo de ejecución de C](../atl/programming-with-atl-and-c-run-time-code.md)  
 Describe las ventajas de la vinculación estática o dinámicamente a la biblioteca de tiempo de ejecución de C (CRT).  
  
 [Programar con CComBSTR](../atl/programming-with-ccombstr-atl.md)  
 Describe varias situaciones que requieren precaución al programar con `CComBSTR`.  
  
 [Referencia de codificación](../atl/atl-encoding-reference.md)  
 Proporciona funciones y macros que admita la codificación en un intervalo común de estándares de Internet, como uuencode, hexadecimal y UTF8 en atlenc.h.  
  
 [Referencia de utilidades](../atl/atl-utilities-reference.md)  
 Proporciona código para manipular las rutas de acceso y las direcciones URL en forma de [CPathT](../atl/reference/cpatht-class.md) y [CUrl](../atl/reference/curl-class.md). Un grupo de subprocesos, [CThreadPool](../atl/reference/cthreadpool-class.md), puede usar en sus propias aplicaciones. Este código se puede encontrar en atlpath.h y atlutil.h.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Ejemplos de ATL](../visual-cpp-samples.md)  
 Proporciona descripciones y vínculos a los programas de ejemplo ATL.  
  
 [Creación de un proyecto ATL](../atl/reference/creating-an-atl-project.md)  
 Contiene información sobre el Asistente para proyectos ATL.  
  
 [Asistente para controles ATL](../atl/reference/atl-control-wizard.md)  
 Describe cómo agregar clases.  
  
 [Programación con atributos](../windows/attributed-programming-concepts.md)  
 Proporciona información general sobre el uso de atributos para simplificar la programación COM y en una lista de vínculos a temas más detallados.  
  
 [Información general de clases ATL](../atl/atl-class-overview.md)  
 Proporciona información de referencia y vínculos a las clases ATL.

