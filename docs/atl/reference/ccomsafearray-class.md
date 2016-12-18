---
title: "Clase CComSafeArray | Microsoft Docs"
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
  - "CComSafeArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComSafeArray (clase)"
ms.assetid: ee349aef-33db-4c85-bd08-5d86a3c9d53a
caps.latest.revision: 26
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clase CComSafeArray
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase es un contenedor de la estructura **SAFEARRAY**.  
  
## Sintaxis  
  
```  
template <  
   typename T,  
   VARTYPE _vartype = _ATL_AutomationType< T >::type  
>  
class CComSafeArray  
```  
  
#### Parámetros  
 `T`  
 Tipo de datos que se va a almacenar en la matriz.  
  
## Miembros  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CComSafeArray::CComSafeArray](../Topic/CComSafeArray::CComSafeArray.md)|El constructor.|  
|[CComSafeArray::~CComSafeArray](../Topic/CComSafeArray::~CComSafeArray.md)|Destructor.|  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CComSafeArray::Add](../Topic/CComSafeArray::Add.md)|Agrega uno o más elementos, o una estructura **SAFEARRAY**, a `CComSafeArray`.|  
|[CComSafeArray::Attach](../Topic/CComSafeArray::Attach.md)|Asocia una estructura **SAFEARRAY** a un objeto `CComSafeArray`.|  
|[CComSafeArray::CopyFrom](../Topic/CComSafeArray::CopyFrom.md)|Copia el contenido de una estructura **SAFEARRAY** en el objeto `CComSafeArray`.|  
|[CComSafeArray::CopyTo](../Topic/CComSafeArray::CopyTo.md)|Crea una copia del objeto `CComSafeArray`.|  
|[CComSafeArray::Create](../Topic/CComSafeArray::Create.md)|Crea un objeto `CComSafeArray`.|  
|[CComSafeArray::Destroy](../Topic/CComSafeArray::Destroy.md)|Destruye un objeto `CComSafeArray`.|  
|[CComSafeArray::Detach](../Topic/CComSafeArray::Detach.md)|Desasocia un elemento **SAFEARRAY** de un objeto `CComSafeArray`.|  
|[CComSafeArray::GetAt](../Topic/CComSafeArray::GetAt.md)|Recupera un único elemento de una matriz unidimensional.|  
|[CComSafeArray::GetCount](../Topic/CComSafeArray::GetCount.md)|Devuelve el número de elementos de la matriz.|  
|[CComSafeArray::GetDimensions](../Topic/CComSafeArray::GetDimensions.md)|Devuelve el número de dimensiones de la matriz.|  
|[CComSafeArray::GetLowerBound](../Topic/CComSafeArray::GetLowerBound.md)|Devuelve el límite inferior de una determinada dimensión de la matriz.|  
|[CComSafeArray::GetSafeArrayPtr](../Topic/CComSafeArray::GetSafeArrayPtr.md)|Devuelve la dirección del miembro de datos `m_psa`.|  
|[CComSafeArray::GetType](../Topic/CComSafeArray::GetType.md)|Devuelve el tipo de datos almacenado en la matriz.|  
|[CComSafeArray::GetUpperBound](../Topic/CComSafeArray::GetUpperBound.md)|Devuelve el límite superior de cualquier dimensión de la matriz.|  
|[CComSafeArray::IsSizable](../Topic/CComSafeArray::IsSizable.md)|Comprueba si se puede cambiar el tamaño de un objeto `CComSafeArray`.|  
|[CComSafeArray::MultiDimGetAt](../Topic/CComSafeArray::MultiDimGetAt.md)|Recupera un único elemento de una matriz multidimensional.|  
|[CComSafeArray::MultiDimSetAt](../Topic/CComSafeArray::MultiDimSetAt.md)|Establece el valor de un elemento de una matriz multidimensional.|  
|[CComSafeArray::Resize](../Topic/CComSafeArray::Resize.md)|Cambia el tamaño de un objeto `CComSafeArray`.|  
|[CComSafeArray::SetAt](../Topic/CComSafeArray::SetAt.md)|Establece el valor de un elemento de una matriz unidimensional.|  
  
### Operadores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CComSafeArray::operator LPSAFEARRAY](../Topic/CComSafeArray::operator%20LPSAFEARRAY.md)|Transmite un valor a un puntero **SAFEARRAY**.|  
|[CComSafeArray::operator](../Topic/CComSafeArray::operator.md)|Recupera un elemento de la matriz.|  
|[CComSafeArray::operator \=](../Topic/CComSafeArray::operator%20=.md)|Operador de asignación.|  
  
### Miembros de datos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CComSafeArray::m\_psa](../Topic/CComSafeArray::m_psa.md)|Este miembro de datos contiene la dirección de la estructura **SAFEARRAY**.|  
  
## Comentarios  
 `CComSafeArray` proporciona un contenedor para la clase [SAFEARRAY Data Type](http://msdn.microsoft.com/es-es/9ec8025b-4763-4526-ab45-390c5d8b3b1e), lo que facilita la creación y administración de matrices unidimensionales y multidimensionales de casi cualquiera de los tipos compatibles VARIANT.  
  
 `CComSafeArray` simplifica el paso de matrices entre procesos y, además, proporciona seguridad adicional al comprobar los valores de índice de matriz con los limites superior e inferior.  
  
 El límite inferior de `CComSafeArray` puede empezar por cualquier valor definido por el usuario, pero las matrices a las que se accede a través de C\+\+ usan un límite inferior de 0. Otros lenguajes como Visual Basic pueden usar otros valores límite \(por ejemplo, de \-10 a 10\).  
  
 Use [CComSafeArray::Create](../Topic/CComSafeArray::Create.md) para crear un objeto `CComSafeArray` y [CComSafeArray::Destroy](../Topic/CComSafeArray::Destroy.md) para eliminarlo.  
  
 Un elemento `CComSafeArray` puede contener el siguiente subconjunto de tipos de datos VARIANT:  
  
|VARTYPE|Descripción|  
|-------------|-----------------|  
|VT\_I1|char|  
|VT\_I2|short|  
|VT\_I4|int|  
|VT\_I4|long|  
|VT\_I8|longlong|  
|VT\_UI1|byte|  
|VT\_UI2|ushort|  
|VT\_UI4|uint|  
|VT\_UI4|ulong|  
|VT\_UI8|ulonglong|  
|VT\_R4|float|  
|VT\_R8|double|  
|VT\_DECIMAL|puntero decimal|  
|VT\_VARIANT|puntero variant|  
|VT\_CY|Currency \(tipo de datos\)|  
  
## Requisitos  
 **Encabezado:** atlsafe.h  
  
## Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#75](../../atl/codesnippet/CPP/ccomsafearray-class_1.cpp)]  
  
## Vea también  
 [SAFEARRAY Data Type](http://msdn.microsoft.com/es-es/9ec8025b-4763-4526-ab45-390c5d8b3b1e)   
 [CComSafeArray::Create](../Topic/CComSafeArray::Create.md)   
 [CComSafeArray::Destroy](../Topic/CComSafeArray::Destroy.md)   
 [Class Overview](../../atl/atl-class-overview.md)