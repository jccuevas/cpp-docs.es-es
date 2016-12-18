---
title: "Modificar el comportamiento de un control en tiempo de ejecuci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Controles ActiveX [C++], comportamiento en tiempo de ejecución"
ms.assetid: 78b44b0f-0d5a-4da0-8aa2-595f5789c634
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Modificar el comportamiento de un control en tiempo de ejecuci&#243;n
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Después de [insertar un control](../../data/ado-rdo/inserting-the-control-into-a-visual-cpp-application.md) y generar una o varias [clases contenedoras](../../data/ado-rdo/wrapper-classes.md), se puede invocar a los métodos del control y programar los controladores de eventos del control.  
  
 Las [clases contenedoras](../../data/ado-rdo/wrapper-classes.md) del control especifican las funciones que puede usarse para modificar el comportamiento del control en tiempo de ejecución. Es necesario incluir el archivo de encabezado de la clase contenedora adecuada y usar los métodos. Para establecer una propiedad, busque un método de descriptor de acceso con el nombre de propiedad con el prefijo Set. Para recuperar una propiedad, busque un método de descriptor de acceso con el nombre de propiedad con el prefijo Get. Los controladores de eventos se pueden escribir más adelante.  
  
 Dado que los controles se implementan mediante automatización, los tipos que se pasan solo pueden ser tipos de automatización seguros, como BSTR y VARIANT. Aunque puede usar llamadas al sistema para asignar y establecer tipos BSTR y VARIANT, puede que quiera usar las clases contenedoras ATL \([CComBSTR](../../atl/reference/ccombstr-class.md), [CComVariant](../../atl/reference/ccomvariant-class.md)\), las clases contenedoras de compatibilidad con el compilador de COM de Visual C\+\+ \([\_bstr\_t](../../cpp/bstr-t-class.md), [\_variant\_t](../../cpp/variant-t-class.md)\) o la clase contenedora de MFC \([COleVariant](../../mfc/reference/colevariant-class.md)\).  
  
 Si agrega un control de datos, el Asistente para insertar controles ActiveX genera clases contenedoras para las coclases del control de datos que administran sus propios objetos de datos internos. Estas clases no incluyen todos los objetos RDO y ADO, sino que representan objetos internos declarados en la biblioteca de tipos.  
  
 Si quiere usar ADO y RDO directamente, debe conectarse a las DLL de ADO o RDO directamente \(Msado15.dll o Msrdo20.dll\), ya sea con las [clases de compatibilidad con COM del compilador](../../cpp/compiler-com-support-classes.md), que admiten la [directiva \#import](../../preprocessor/preprocessor-directives.md), o mediante el SDK correspondiente.  
  
## Para establecer las propiedades de un control en tiempo de ejecución  
 Tenga en cuenta que algunas propiedades de un control ActiveX pueden ser de solo lectura en tiempo de ejecución, lo que dificulta la creación dinámica. Puede simular temporalmente el modo de diseño para la inicialización de propiedades reemplazando el controlador [OnAmbientPropertyChange](../Topic/COleControl::OnAmbientPropertyChange.md) del contenedor del control, como se describe en el artículo de Knowledge Base, "Cómo: establecer propiedades de tiempo de diseño de controles ActiveX en tiempo de ejecución \(Q260744\)". Encontrará artículos de Knowledge Base en [http:\/\/support.microsoft.com\/](http://support.microsoft.com/).  
  
## Vea también  
 [Utilizar controles ActiveX](../../data/ado-rdo/using-activex-controls.md)