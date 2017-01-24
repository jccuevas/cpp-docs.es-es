---
title: "CSimpleStringT Class | Microsoft Docs"
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
  - "ATL.CSimpleStringT"
  - "ATL::CSimpleStringT"
  - "ATL::CSimpleStringT<BaseType>"
  - "ATL.CSimpleStringT<BaseType>"
  - "CSimpleStringT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleStringT class"
  - "shared classes, CSimpleStringT"
  - "cadenas [C++], ATL (clase)"
ms.assetid: 15814fcb-5b8f-4425-a97e-3b61fc9b48d8
caps.latest.revision: 19
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSimpleStringT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase representa un objeto de `CSimpleStringT` .  
  
## Sintaxis  
  
```  
  
      template <typename   
      BaseType  
      >  
class CSimpleStringT  
```  
  
#### Parámetros  
 `BaseType`  
 El tipo de caracteres de la clase de cadena.  Puede ser una de las siguientes:  
  
-   `char` \(para las cadenas de caracteres ANSI\).  
  
-   `wchar_t` \(para las cadenas de caracteres Unicode\).  
  
-   **TCHAR** \(para ANSI y las cadenas de caracteres Unicode\).  
  
## Members  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSimpleStringT::PCXSTR](../Topic/CSimpleStringT::PCXSTR.md)|un puntero a una cadena constante.|  
|[CSimpleStringT::PXSTR](../Topic/CSimpleStringT::PXSTR.md)|un puntero a una cadena.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSimpleStringT::CSimpleStringT](../Topic/CSimpleStringT::CSimpleStringT.md)|Crea los objetos de `CSimpleStringT` de varias maneras.|  
|[CSimpleStringT::~CSimpleStringT](../Topic/CSimpleStringT::~CSimpleStringT.md)|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSimpleStringT::Append](../Topic/CSimpleStringT::Append.md)|Agrega un objeto de `CSimpleStringT` a un objeto existente de `CSimpleStringT` .|  
|[CSimpleStringT::AppendChar](../Topic/CSimpleStringT::AppendChar.md)|anexa un carácter a un objeto existente de `CSimpleStringT` .|  
|[CSimpleStringT::CopyChars](../Topic/CSimpleStringT::CopyChars.md)|Copia un carácter o caracteres a otros cadena.|  
|[CSimpleStringT::CopyCharsOverlapped](../Topic/CSimpleStringT::CopyCharsOverlapped.md)|Copia un carácter o caracteres a otra cadena en la que los búferes se superpongan.|  
|[CSimpleStringT::Empty](../Topic/CSimpleStringT::Empty.md)|Fuerza una cadena para tener una longitud de cero.|  
|[CSimpleStringT::FreeExtra](../Topic/CSimpleStringT::FreeExtra.md)|Libera cualquier memoria adicional asignada previamente por el objeto de cadena.|  
|[CSimpleStringT::GetAllocLength](../Topic/CSimpleStringT::GetAllocLength.md)|Recupera la longitud asignada de un objeto de `CSimpleStringT` .|  
|[CSimpleStringT::GetAt](../Topic/CSimpleStringT::GetAt.md)|Devuelve el carácter en una posición determinada.|  
|[CSimpleStringT::GetBuffer](../Topic/CSimpleStringT::GetBuffer.md)|Devuelve un puntero a caracteres en `CSimpleStringT`.|  
|[CSimpleStringT::GetBufferSetLength](../Topic/CSimpleStringT::GetBufferSetLength.md)|Devuelve un puntero a caracteres en `CSimpleStringT`, truncando con la longitud especificada.|  
|[CSimpleStringT::GetLength](../Topic/CSimpleStringT::GetLength.md)|Devuelve el número de caracteres de un objeto de `CSimpleStringT` .|  
|[CSimpleStringT::GetManager](../Topic/CSimpleStringT::GetManager.md)|Recupera el administrador de memoria del objeto de `CSimpleStringT` .|  
|[CSimpleStringT::GetString](../Topic/CSimpleStringT::GetString.md)|Recupera la cadena de caracteres|  
|[CSimpleStringT::IsEmpty](../Topic/CSimpleStringT::IsEmpty.md)|Prueba si un objeto de `CSimpleStringT` no contiene ningún carácter.|  
|[CSimpleStringT::LockBuffer](../Topic/CSimpleStringT::LockBuffer.md)|Deshabilita el recuento de referencias y protege la cadena en el búfer.|  
|[CSimpleStringT::Preallocate](../Topic/CSimpleStringT::Preallocate.md)|Asigna una cierta cantidad de memoria para el búfer del carácter.|  
|[CSimpleStringT::ReleaseBuffer](../Topic/CSimpleStringT::ReleaseBuffer.md)|Control de versiones de búfer devuelto por `GetBuffer`.|  
|[CSimpleStringT::ReleaseBufferSetLength](../Topic/CSimpleStringT::ReleaseBufferSetLength.md)|Control de versiones de búfer devuelto por `GetBuffer`.|  
|[CSimpleStringT::SetAt](../Topic/CSimpleStringT::SetAt.md)|Establece un carácter en una posición determinada.|  
|[CSimpleStringT::SetManager](../Topic/CSimpleStringT::SetManager.md)|Establece el administrador de memoria de un objeto de `CSimpleStringT` .|  
|[CSimpleStringT::SetString](../Topic/CSimpleStringT::SetString.md)|Establece la cadena de un objeto de `CSimpleStringT` .|  
|[CSimpleStringT::StringLength](../Topic/CSimpleStringT::StringLength.md)|Devuelve el número de caracteres de la cadena especificada.|  
|[CSimpleStringT::Truncate](../Topic/CSimpleStringT::Truncate.md)|Trunca la cadena con una longitud especificada.|  
|[CSimpleStringT::UnlockBuffer](../Topic/CSimpleStringT::UnlockBuffer.md)|Habilita la referencia que cuenta y libera la cadena en el búfer.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSimpleStringT::operator PCXSTR](../Topic/CSimpleStringT::operator%20PCXSTR.md)|Tiene acceso directamente a los caracteres almacenados en un objeto de `CSimpleStringT` como una cadena de lenguaje c.|  
|[CSimpleStringT::operator](../Topic/CSimpleStringT::operator.md)|Devuelve el carácter en una posición determinada — sustitución de operador para `GetAt`.|  
|[CSimpleStringT::operator \+\=](../Topic/CSimpleStringT::operator%20+=.md)|Concatena una nueva cadena al final de una cadena existente.|  
|[CSimpleStringT::operator \=](../Topic/CSimpleStringT::operator%20=.md)|asigna un nuevo valor a un objeto de `CSimpleStringT` .|  
  
## Comentarios  
 `CSimpleStringT` es la clase base para los diversos tipos de cadena compatibles con Visual C\+\+.  Proporciona compatibilidad mínimo para la administración de memoria del objeto string y manipulación básica del búfer.  Para objetos de cadena más avanzados, vea [clase de CStringT](../../atl-mfc-shared/reference/cstringt-class.md).  
  
## Requisitos  
 **encabezado:** atlsimpstr.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)