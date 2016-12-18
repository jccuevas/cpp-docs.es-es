---
title: "CDumpContext Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDumpContext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AfxDump object"
  - "CDumpContext class"
  - "diagnóstico, diagnostic classes"
  - "diagnostic classes"
  - "diagnóstico, diagnostic classes"
ms.assetid: 98c52b2d-14b5-48ed-b423-479a4d1c60fa
caps.latest.revision: 20
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDumpContext Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Admite la salida secuencia\-orientada de diagnóstico en forma de texto legible.  
  
## Sintaxis  
  
```  
class CDumpContext  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDumpContext::CDumpContext](../Topic/CDumpContext::CDumpContext.md)|Crea un objeto `CDumpContext`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDumpContext::DumpAsHex](../Topic/CDumpContext::DumpAsHex.md)|vuelca el elemento indicado en formato hexadecimal.|  
|[CDumpContext::Flush](../Topic/CDumpContext::Flush.md)|Vacía los datos en el búfer de contexto de volcado de memoria.|  
|[CDumpContext::GetDepth](../Topic/CDumpContext::GetDepth.md)|Obtiene un entero correspondiente a la profundidad de volcado de memoria.|  
|[CDumpContext::HexDump](../Topic/CDumpContext::HexDump.md)|Bytes de los volcados contenido en una matriz en formato hexadecimal.|  
|[CDumpContext::SetDepth](../Topic/CDumpContext::SetDepth.md)|Establece la profundidad de volcado de memoria.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDumpContext::operator \<\<](../Topic/CDumpContext::operator%20%3C%3C.md)|Inserta variables y objetos en el contexto de volcado de memoria.|  
  
## Comentarios  
 `CDumpContext` no tiene una clase base.  
  
 Puede utilizar [afxDump](../Topic/afxDump%20\(CDumpContext%20in%20MFC\).md), un objeto predeclared de `CDumpContext` , para la mayoría de volcar.  El objeto de `afxDump` sólo está disponible en la versión de depuración de la biblioteca Microsoft Foundation Class.  
  
 Varios de uso `afxDump` de [servicios de diagnóstico](../../mfc/reference/diagnostic-services.md) de memoria para su salida.  
  
 En un entorno de Windows, enrutan a la salida del objeto predefinido de `afxDump` , conceptualmente similar a la secuencia de `cerr` , el depurador mediante la función de Windows **OutputDebugString**.  
  
 La clase de `CDumpContext` tiene un operador sobrecargado de inserción \(**\<\<**\) para punteros de `CObject` que vuelque los datos de objeto.  Si necesita un formato de volcado personalizado para un objeto derivado, reemplace [CObject:: volcado](../Topic/CObject::Dump.md).  La mayoría de las clases base de Microsoft implementan una función invalidada de miembro de `Dump` .  
  
 Las clases que no son derivadas de `CObject`, como `CString`, `CTime`, y `CTimeSpan`, tienen sus propios operadores sobrecargados de inserción de `CDumpContext` , así como las estructuras a menudo como **CFileStatus**, `CPoint`, y `CRect`.  
  
 Si utiliza [IMPLEMENT\_DYNAMIC](../Topic/IMPLEMENT_DYNAMIC.md) o macro de [IMPLEMENT\_SERIAL](../Topic/IMPLEMENT_SERIAL.md) en la implementación de la clase, después `CObject::Dump` imprimirá el nombre de `CObject`\- clase derivada.  si no, imprimirá `CObject`.  
  
 La clase de `CDumpContext` está disponible con las versiones de depuración y de lanzamiento de la biblioteca, pero la función miembro de `Dump` se define sólo en la versión de depuración.  Utilice **\_DEBUG \#ifdef** y las instrucciones de `#endif` el corchete el código de diagnóstico, incluido el miembro de `Dump` personalizados de funciona.  
  
 Antes de crear posee el objeto de `CDumpContext` , debe crear un objeto de `CFile` que actúa como el destino de volcado de memoria.  
  
 Para obtener más información sobre `CDumpContext`, vea [Aplicaciones MFC de depuración](../Topic/MFC%20Debugging%20Techniques.md).  
  
 **\_DEBUG \#define**  
  
## Jerarquía de herencia  
 `CDumpContext`  
  
## Requisitos  
 **encabezado:** afx.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CFile Class](../../mfc/reference/cfile-class.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)