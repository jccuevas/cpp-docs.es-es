---
title: "CGopherLocator Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CGopherLocator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CGopherLocator class"
  - "gopher locator"
  - "Internet, gopher searches"
ms.assetid: 6fcc015f-5ae6-4959-b936-858634c71019
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CGopherLocator Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene gopher “localizador” de un servidor gopher, determina el tipo locator, y coloca el localizador a disposición [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md).  
  
> [!NOTE]
>  Se han dejado de utilizar las clases `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` y sus miembros porque no funcionan en la plataforma de Windows XP, pero seguirán funcionando en plataformas anteriores.  
  
## Sintaxis  
  
```  
class CGopherLocator : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CGopherLocator::CGopherLocator](../Topic/CGopherLocator::CGopherLocator.md)|Crea un objeto `CGopherLocator`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CGopherLocator::GetLocatorType](../Topic/CGopherLocator::GetLocatorType.md)|Analiza un localizador de gopher y determina los atributos.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CGopherLocator::operator LPCTSTR](../Topic/CGopherLocator::operator%20LPCTSTR.md)|Tiene acceso directamente a los caracteres almacenados en un objeto de `CGopherLocator` como una cadena de lenguaje c.|  
  
## Comentarios  
 Una aplicación debe obtener el localizador de un servidor gopher antes de poder recuperar información de ese servidor.  Una vez que tiene el atributo locator, debe tratar el localizador como símbolo opaco.  
  
 Cada llamada de gopher tiene atributos que determinan el tipo de archivo o servidor encontrado.  Vea [GetLocatorType](../Topic/CGopherLocator::GetLocatorType.md) para obtener una lista de tipos de ubicadores de gopher.  
  
 Una aplicación utiliza normalmente el localizador para las llamadas a [CGopherFileFind:: FindFile](../Topic/CGopherFileFind::FindFile.md) para recuperar un fragmento específico.  
  
 Para obtener más información sobre cómo `CGopherLocator` funciona con las clases de internet de MFC, vea el artículo [Internet que programa con WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CGopherLocator`  
  
## Requisitos  
 **encabezado:** afxinet.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CGopherFileFind Class](../../mfc/reference/cgopherfilefind-class.md)