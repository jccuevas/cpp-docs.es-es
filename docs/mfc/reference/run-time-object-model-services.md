---
title: "Servicios del modelo de objetos en tiempo de ejecuci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "macros de servicios del modelo de objetos en tiempo de ejecución"
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# Servicios del modelo de objetos en tiempo de ejecuci&#243;n
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las clases [CObject](../../mfc/reference/cobject-class.md) y [Recursos](../../mfc/reference/cruntimeclass-structure.md) encapsulan varios servicios de objeto, incluido el acceso a la información de la clase en tiempo de ejecución, la serialización, y la creación de objetos dinámica.  Todas las clases derivadas de `CObject` heredan esta funcionalidad.  
  
 Acceso a la información de la clase en tiempo de ejecución permite determinar información sobre una clase de objeto en tiempo de ejecución.  La capacidad de determinar el tipo de un objeto en tiempo de ejecución es útil si necesita la comprobación de tipo adicional de los argumentos de la función y cuando debe escribir el código especial basado en la clase de un objeto.  La información de la clase en tiempo de ejecución no se admite directamente en el lenguaje C\+\+.  
  
 La serialización es el proceso de escritura o lectura el contenido de un objeto de o desde un archivo.  Puede usar la serialización para almacenar el contenido de un objeto incluso después de cerrar la aplicación.  El objeto se puede leer del archivo cuando se reinicia la aplicación.  Estos objetos de datos se “persistentes.”  
  
 La creación de objetos dinámica permite crear un objeto de una clase especificada en tiempo de ejecución.  Por ejemplo, el documento, la vista, y los objetos de cuadro deben admitir la creación dinámica porque el marco necesario crearlos dinámicamente.  
  
 La tabla siguiente muestra las macros MFC que información admiten la clase en tiempo de ejecución, serialización, y creación dinámica.  
  
 Para obtener más información sobre estos servicios y la serialización de objetos en tiempo de ejecución, vea el artículo [Clase de CObject: Información de acceso de la clase en tiempo de ejecución](../../mfc/accessing-run-time-class-information.md).  
  
### Macros de los servicios del modelo de objetos en tiempo de ejecución  
  
|||  
|-|-|  
|[DECLARE\_DYNAMIC](../Topic/DECLARE_DYNAMIC.md)|Permite el acceso a la información de la clase en tiempo de ejecución \(se utiliza en la declaración de clase\).|  
|[DECLARE\_DYNCREATE](../Topic/DECLARE_DYNCREATE.md)|Habilita la creación dinámica y el acceso a la información de la clase en tiempo de ejecución \(se utiliza en la declaración de clase\).|  
|[DECLARE\_SERIAL](../Topic/DECLARE_SERIAL.md)|Habilita la serialización y el acceso a la información de la clase en tiempo de ejecución \(se utiliza en la declaración de clase\).|  
|[IMPLEMENT\_DYNAMIC](../Topic/IMPLEMENT_DYNAMIC.md)|Permite el acceso a la información de la clase en tiempo de ejecución \(se utiliza en la implementación de la clase\).|  
|[IMPLEMENT\_DYNCREATE](../Topic/IMPLEMENT_DYNCREATE.md)|Habilita la creación dinámica y el acceso a la información en tiempo de ejecución \(se utiliza en la implementación de la clase\).|  
|[IMPLEMENT\_SERIAL](../Topic/IMPLEMENT_SERIAL.md)|Permite la serialización y el acceso a la información de la clase en tiempo de ejecución \(se utiliza en la implementación de la clase\).|  
|[RUNTIME\_CLASS](../Topic/RUNTIME_CLASS.md)|Devuelve la estructura de `CRuntimeClass` que corresponde a la clase denominada.|  
  
 OLE normalmente requiere la creación dinámica de objetos en tiempo de ejecución.  Por ejemplo, una aplicación de servidor OLE debe poder crear elementos OLE dinámicamente en respuesta a una solicitud de un cliente.  Igualmente, un servidor de automatización debe poder crear elementos en respuesta a solicitudes de clientes de automatización.  
  
 La biblioteca Microsoft Foundation Class proporciona dos macros específicas de OLE.  
  
### Creación dinámica de objetos OLE  
  
|||  
|-|-|  
|[DECLARE\_OLECREATE](../Topic/DECLARE_OLECREATE.md)|Habilita los objetos que se van a crear con la automatización OLE.|  
|[IMPLEMENT\_OLECREATE](../Topic/IMPLEMENT_OLECREATE.md)|Habilita los objetos que se van a crear por el sistema OLE.|  
  
## Vea también  
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)