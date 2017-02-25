---
title: "Conceptos de Active Template Library (ATL) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, acerca de ATL"
ms.assetid: a3960991-4d76-4da5-9568-3fa7fde53ff4
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# Conceptos de Active Template Library (ATL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Active \(ATL\) Template Library es un conjunto de clases de C\+\+ basadas en plantillas que permiten crear objetos pequeños, rápidos \(COM\) del modelo de objetos componentes.  Tiene compatibilidad especial para características COM clave, incluidas las implementaciones comunes, interfaces duales, interfaces COM estándar de enumeradores, puntos de conexión, rasga interfaces, y controles ActiveX.  
  
 Si tiene muchos programación ATL, deseará obtener más información sobre atributos, una característica nueva de Visual C\+\+ .NET que está diseñado para simplificar la programación COM.  Para obtener más información, vea [Programación con atributos](../windows/attributed-programming-concepts.md).  
  
## En esta sección  
 [tutorial de ATL](../atl/active-template-library-atl-tutorial.md)  
 Este tutorial le ayuda a crear un control y en el proceso le enseña los fundamentos de ATL.  
  
 [introducción a COM y a ATL](../atl/introduction-to-com-and-atl.md)  
 Presenta los principales conceptos detrás del modelo de objetos \(COM\) componentes.  Este artículo también explica brevemente qué es ATL y cuando debe utilizarlo.  
  
 [Fundamentos de objetos COM de ATL](../atl/fundamentals-of-atl-com-objects.md)  
 Explica la relación entre distintas clases ATL y cómo se implementan las clases.  
  
 [interfaces duales y ATL](../atl/dual-interfaces-and-atl.md)  
 Describe interfaces duales desde una perspectiva de ATL.  
  
 [Colecciones y enumeradores ATL](../atl/atl-collections-and-enumerators.md)  
 Describe la implementación y la creación de colecciones de enumeradores en ATL.  
  
 [Fundamentales compuestos de Control](../atl/atl-composite-control-fundamentals.md)  
 Proporciona instrucciones paso a paso para crear un control compuesto.  Un control compuesto es un tipo de control ActiveX que puede contener otros controles ActiveX o controles de Windows.  
  
 [Preguntas más frecuentes sobre la contención de controles ATL](../atl/atl-control-containment-faq.md)  
 Trata las preguntas fundamentales relacionadas con hospedar controles con ATL.  
  
 [Páginas de propiedades ATL COM](../atl/atl-com-property-pages.md)  
 Muestra cómo especificar e implementar páginas de propiedades COM.  
  
 [Compatibilidad ATL para Controles de DHTML](../atl/atl-support-for-dhtml-controls.md)  
 Proporciona instrucciones paso a paso para crear un control DHTML.  
  
 [Puntos de conexión ATL](../atl/atl-connection-points.md)  
 Explica qué son los puntos de conexión y cómo ATL se implementan.  
  
 [control de eventos y ATL](../atl/event-handling-and-atl.md)  
 Describe los pasos que debe seguir para controlar eventos COM mediante clases de [IDispEventImpl](../atl/reference/idispeventimpl-class.md) y de [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) ATL.  
  
 [ATL y el Threaded libre Contador](../atl/atl-and-the-free-threaded-marshaler.md)  
 Proporciona detalles sobre la opción ATL Simple del asistente para objetos que permite que la clase agregue el contador de subproceso libre \(FTM\).  
  
 [Especificar el modelo de subprocesos de proyecto](../atl/specifying-the-threading-model-for-a-project-atl.md)  
 Describe las macros disponibles controlar el tiempo de ejecución relacionado con el rendimiento al subprocesamiento en el proyecto.  
  
 [Clases de módulo ATL](../atl/atl-module-classes.md)  
 Describe clases de módulo nuevas para ATL 7,0.  Las clases de módulo implementan la funcionalidad básica necesaria para ATL.  
  
 [servicios de ATL](../atl/atl-services.md)  
 Trata la serie de eventos que se producen cuando se implementa un servicio.  También habla de algunos de los conceptos relacionados con el desarrollo de un servicio.  
  
 [Clases de ventana ATL](../atl/atl-window-classes.md)  
 Describe cómo crear, crear superclase, y crear subclases las ventanas en ATL.  Las clases de ventana ATL no son clases COM.  
  
 [Clases de la colección ATL](../atl/atl-collection-classes.md)  
 Describe cómo utilizar matrices y asignaciones en ATL.  
  
 [El componente de registro ATL \(registro\)](../atl/atl-registry-component-registrar.md)  
 Describe la sintaxis de script ATL y parámetros reemplazables.  También explica cómo configurar un vínculo estático al registro.  
  
 [Programación con código en tiempo de ejecución de ATL y c](../atl/programming-with-atl-and-c-run-time-code.md)  
 Describe las ventajas de la vinculación estática o dinámicamente a la biblioteca en tiempo de ejecución de C \(CRT\).  
  
 [programación con CComBSTR](../atl/programming-with-ccombstr-atl.md)  
 Describe varias situaciones que requieren para advertir al programar con `CComBSTR`.  
  
 [Referencia de codificación](../atl/atl-encoding-reference.md)  
 Proporciona funciones y macros que codificación support en un intervalo de estándares de internet comunes como uuencode, hexadecimal, y UTF8 en atlenc.h.  
  
 [Referencia de utilidades](../atl/atl-utilities-reference.md)  
 Proporciona código para las rutas y las direcciones URL de manipulación en forma de [CPathT](../atl/reference/cpatht-class.md) y [rizo](../atl/reference/curl-class.md).  Un grupo de subprocesos, [CThreadPool](../atl/reference/cthreadpool-class.md), se puede utilizar en dispone de aplicaciones.  Este código se encuentra en atlpath.h y atlutil.h.  
  
## Secciones relacionadas  
 [ejemplos de ATL](../top/visual-cpp-samples.md)  
 Proporciona descripciones de y vínculos a los programas de ejemplo ATL.  
  
 [Crear un proyecto ATL](../atl/reference/creating-an-atl-project.md)  
 Contiene información sobre el asistente para proyectos ATL.  
  
 [Asistente para controles ATL](../atl/reference/atl-control-wizard.md)  
 Explica cómo agregar clases.  
  
 [Programación con atributos](../windows/attributed-programming-concepts.md)  
 Proporciona información general sobre cómo utilizar atributos para simplificar la programación COM más una lista de vínculos a temas más detallados.  
  
 [Información general de la clase ATL](../atl/atl-class-overview.md)  
 Proporciona información y vínculos de referencia a las clases ATL.