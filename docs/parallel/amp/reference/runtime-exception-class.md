---
title: runtime_exception (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- runtime_exception
- AMPRT/runtime_exception
- AMPRT/Concurrency::runtime_exception
- AMPRT/Concurrency::runtime_exception::get_error_code
dev_langs:
- C++
helpviewer_keywords:
- runtime_exception class
ms.assetid: 8fe3ce2c-3d4c-4b9c-95e8-e592f37adefd
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 399d2531c06285012df12d703b4cda6e18469c38
ms.lasthandoff: 03/17/2017

---
# <a name="runtimeexception-class"></a>runtime_exception (Clase)
El tipo base para excepciones de la biblioteca de C++ Accelerated Massive Parallelism (AMP).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
class runtime_exception : public std::exception;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[runtime_exception (Constructor)](#ctor)|Inicializa una nueva instancia de la clase `runtime_exception`.|  
|[~ runtime_exception (destructor)](#dtor)|Destruye el objeto `runtime_exception`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[get_error_code](#runtime_exception__get_error_code)|Devuelve el código de error que provocó la excepción.|  

  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[operator=](#operator_eq)|Copia el contenido del elemento `runtime_exception` objeto en éste.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `exception`  
  
 `runtime_exception`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amprt.h  
  
 **Espacio de nombres:** Concurrency  

## <a name="runtime_exception__ctor"></a>runtime_exception (Constructor)  
Inicializa una nueva instancia de la clase.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
runtime_exception(  
    const char * _Message,  
    HRESULT _Hresult ) throw();  
  
explicit runtime_exception(  
    HRESULT _Hresult ) throw();  
  
runtime_exception(  
    const runtime_exception & _Other ) throw();  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Message`  
 Una descripción del error que provocó la excepción.  
  
 `_Hresult`  
 El valor HRESULT de error que provocó la excepción.  
  
 `_Other`  
 La `runtime_exception` objeto que se va a copiar.  
  
### <a name="return-value"></a>Valor devuelto  
 Objeto `runtime_exception`.  

## <a name="dtor"></a>~ runtime_exception (destructor)  
Destruye el objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
virtual ~runtime_exception() throw();  
```  
  
## <a name="runtime_exception__get_error_code"></a>get_error_code   
Devuelve el código de error que provocó la excepción.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
HRESULT get_error_code() const throw();  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor HRESULT de error que provocó la excepción.  
  
## <a name="runtime_exception__operator_eq"></a>  operator=   
  Copia el contenido del elemento `runtime_exception` objeto en éste.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
runtime_exception & operator= (    const runtime_exception & _Other ) throw();  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `runtime_exception` objeto que se va a copiar.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a este `runtime_exception` objeto.  
  

  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)

