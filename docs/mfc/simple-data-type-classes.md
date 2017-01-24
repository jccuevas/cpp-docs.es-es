---
title: "Clases de tipos de datos simples | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases de datos [C++]"
  - "clases escalares [C++]"
  - "clases de tipos de datos simples"
ms.assetid: 0d591d68-0a33-49e9-8a6d-90c90de5c16a
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clases de tipos de datos simples
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las clases siguientes encapsulan las coordenadas del gráfico, cadenas de caracteres, e información de hora y fecha, que permite el uso apropiado de la sintaxis de C\+\+.  Estos objetos se utilizan ampliamente como parámetros a las funciones miembro de clases de Windows en la biblioteca de clases.  Dado que `CPoint`, `CSize`, y `CRect` corresponden a **POINT**, a **TAMAÑO**, y estructuras de `RECT` , respectivamente, en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)], puede utilizar objetos de estas clases de C\+\+ donde puede utilizar estas estructuras del lenguaje C.  Las clases proporcionan interfaces útiles con sus funciones miembro.  `CStringT` proporciona cadenas de caracteres dinámicas muy flexibles.  `CTime`, `COleDateTime`, `CTimeSpan`, y **COleTimeSpan** representan hora y valores de fecha.  Para obtener más información sobre estas clases, vea el artículo [Fecha y hora](../atl-mfc-shared/date-and-time.md).  
  
 Las clases que comienzan con “**COle**” son encapsulaciones de los tipos de datos proporcionados por OLE.  Estos tipos de datos se pueden utilizar en programas de Windows independientemente de otras características OLE se utilizan.  
  
 [Clase de CStringT](../atl-mfc-shared/reference/cstringt-class.md)  
 Contiene las cadenas de caracteres.  
  
 [CTime](../atl-mfc-shared/reference/ctime-class.md)  
 Contiene la hora absoluta y valores de fecha.  
  
 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)  
 Contenedor para el tipo **date**de automatización OLE.  Representa valores de fecha y hora.  
  
 [CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md)  
 Contiene la hora y valores de fecha relativos.  
  
 [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)  
 Contiene los valores relativos de `COleDateTime` , como la diferencia entre dos valores de `COleDateTime` .  
  
 [CPoint](../atl-mfc-shared/reference/cpoint-class.md)  
 Contiene las coordenadas \(x, y\) los pares.  
  
 [CSize](../atl-mfc-shared/reference/csize-class.md)  
 Contiene distancia, posiciones relativas, o valores emparejados.  
  
 [CRect](../atl-mfc-shared/reference/crect-class.md)  
 Contiene coordenadas de áreas rectangulares.  
  
 [CImageList](../mfc/reference/cimagelist-class.md)  
 Proporciona la funcionalidad de la lista de imágenes de Windows.  Las listas de imágenes se utilizan con los controles de lista y los controles de árbol.  También pueden utilizar para almacenar y almacenar un conjunto de mapas de bits mismo\- ordenados.  
  
 [COleVariant](../mfc/reference/colevariant-class.md)  
 Contenedor para el tipo **VARIANT**de automatización OLE.  Los datos en s para **VARIANT**pueden almacenarse en muchos formatos.  
  
 [COleCurrency](../mfc/reference/colecurrency-class.md)  
 El contenedor de la automatización OLE escribe **DIVISA**, tipo de punto fijo de la aritmética, con 15 dígitos antes del separador decimal y 4 dígitos después.  
  
> [!NOTE]
>  A partir de Visual C\+\+ .NET, `CRect`, `CSize`, y `CPoint` se han modificado para utilizar en ATL o aplicaciones MFC.  Además, `CStringT` se ha agregado para proporcionar una MFC\- independiente `CString`\- como clase.  Para obtener más información sobre clases de utilidad compartidas, vea [Clases compartidas](../atl-mfc-shared/atl-mfc-shared-classes.md).  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)