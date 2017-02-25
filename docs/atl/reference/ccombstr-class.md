---
title: "CComBSTR (clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CComBSTR"
  - "CComBSTR"
  - "ATL.CComBSTR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BSTR, contenedoras"
  - "CComBSTR"
  - "CComBSTR (clase)"
ms.assetid: 8fea1879-a05e-47a5-a803-8dec60eaa534
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CComBSTR (clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase es un contenedor para s para `BSTR`.  
  
## Sintaxis  
  
```  
  
class CComBSTR  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComBSTR::CComBSTR](../Topic/CComBSTR::CComBSTR.md)|el constructor.|  
|[CComBSTR::~CComBSTR](../Topic/CComBSTR::~CComBSTR.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComBSTR::Append](../Topic/CComBSTR::Append.md)|anexa una cadena a `m_str`.|  
|[CComBSTR::AppendBSTR](../Topic/CComBSTR::AppendBSTR.md)|anexa `BSTR` a `m_str`.|  
|[CComBSTR::AppendBytes](../Topic/CComBSTR::AppendBytes.md)|anexa un número de bytes especificado a `m_str`.|  
|[CComBSTR::ArrayToBSTR](../Topic/CComBSTR::ArrayToBSTR.md)|Crea `BSTR` del primer carácter de cada elemento del safearray y lo asocia al objeto de `CComBSTR` .|  
|[CComBSTR::AssignBSTR](../Topic/CComBSTR::AssignBSTR.md)|asigna `BSTR` a `m_str`.|  
|[CComBSTR::Attach](../Topic/CComBSTR::Attach.md)|Asocia `BSTR` al objeto de `CComBSTR` .|  
|[CComBSTR::BSTRToArray](../Topic/CComBSTR::BSTRToArray.md)|Crea un safearray unidimensional basada en cero, donde es un carácter cada elemento de matriz de objetos de `CComBSTR` .|  
|[CComBSTR::ByteLength](../Topic/CComBSTR::ByteLength.md)|devuelve la longitud de `m_str` en bytes.|  
|[CComBSTR::Copy](../Topic/CComBSTR::Copy.md)|devuelve una copia de `m_str`.|  
|[CComBSTR::CopyTo](../Topic/CComBSTR::CopyTo.md)|Devuelve una copia de `m_str` mediante un parámetro de **\[out\]**|  
|[CComBSTR::Detach](../Topic/CComBSTR::Detach.md)|Desasocia `m_str` del objeto de `CComBSTR` .|  
|[CComBSTR::Empty](../Topic/CComBSTR::Empty.md)|libera `m_str`.|  
|[CComBSTR::Length](../Topic/CComBSTR::Length.md)|devuelve la longitud de `m_str`.|  
|[CComBSTR::LoadString](../Topic/CComBSTR::LoadString.md)|carga un recurso de cadena.|  
|[CComBSTR::ReadFromStream](../Topic/CComBSTR::ReadFromStream.md)|carga un objeto de `BSTR` de una secuencia.|  
|[CComBSTR::ToLower](../Topic/CComBSTR::ToLower.md)|Convierte la cadena en minúsculas.|  
|[CComBSTR::ToUpper](../Topic/CComBSTR::ToUpper.md)|Convierte la cadena a mayúsculas.|  
|[CComBSTR::WriteToStream](../Topic/CComBSTR::WriteToStream.md)|Guarda `m_str` en una secuencia.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComBSTR::operator BSTR](../Topic/CComBSTR::operator%20BSTR.md)|Convierte un objeto de `CComBSTR` a `BSTR`.|  
|[CComBSTR::operator \!](../Topic/CComBSTR::operator%20!.md)|devuelve `true` o `false`, dependiendo de si `m_str`es `NULL`.|  
|[CComBSTR::operator \!\=](../Topic/CComBSTR::operator%20!=.md)|compara `CComBSTR` con una cadena.|  
|[CComBSTR::operator &](../Topic/CComBSTR::operator%20&.md)|Devuelve la dirección de `m_str`.|  
|[CComBSTR::operator \+\=](../Topic/CComBSTR::operator%20+=.md)|Anexa `CComBSTR` al objeto.|  
|[CComBSTR::operator \<](../Topic/CComBSTR::operator%20%3C.md)|compara `CComBSTR` con una cadena.|  
|[CComBSTR::operator \=](../Topic/CComBSTR::operator%20=.md)|asigna un valor a `m_str`.|  
|[CComBSTR::operator \=\=](../Topic/CComBSTR::operator%20==.md)|compara `CComBSTR` con una cadena.|  
|[CComBSTR::operator \>](../Topic/CComBSTR::operator%20%3E.md)|compara `CComBSTR` con una cadena.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComBSTR::m\_str](../Topic/CComBSTR::m_str.md)|contiene `BSTR` asociado con el objeto de `CComBSTR` .|  
  
## Comentarios  
 La clase de `CComBSTR` es un contenedor para s para `BSTR`, que son cadenas longitud\-prefijadas.  La longitud se almacena como entero en la ubicación de memoria que precede a los datos de la cadena.  
  
 [BSTR](http://msdn.microsoft.com/es-es/1b2d7d2c-47af-4389-a6b6-b01b7e915228) terminado en null cuando el carácter contado último pero también pueda contener caracteres null incrustados dentro de la cadena.  La longitud de la cadena está determinada por el recuento de caracteres, no el primer carácter nulo.  
  
> [!NOTE]
>  La clase de `CComBSTR` proporciona varios miembros \(constructores, operadores de asignación, y operadores de comparación\) que toma ANSI o cadenas Unicode como argumentos.  Las versiones ANSI de estas funciones son menos eficaces que sus homólogos de Unicode porque las cadenas Unicode temporales se crean a menudo internamente.  Para aumentar la eficacia, utilice las versiones Unicode cuando sea posible.  
  
> [!NOTE]
>  Debido al comportamiento mejorado de búsqueda implementado en Visual Studio .NET, el código como `bstr = L"String2" + bstr;`, que pueden tener compilado en versiones anteriores, se debe en su lugar implementar como `bstr = CStringW(L"String2") + bstr`.  
  
 Para obtener una lista de precauciones al utilizar `CComBSTR`, vea [programación con CComBSTR](../../atl/programming-with-ccombstr-atl.md).  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)   
 [ATL and MFC String Conversion Macros](../Topic/ATL%20and%20MFC%20String%20Conversion%20Macros.md)