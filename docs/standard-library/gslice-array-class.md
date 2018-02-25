---
title: gslice_array (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- valarray/std::gslice_array
dev_langs:
- C++
helpviewer_keywords:
- gslice_array class
ms.assetid: ad1b4514-b14a-4baf-a293-d5a8e8674c75
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f47b1ce767a2090e718406585d2c40db2c4c8bcb
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="gslicearray-class"></a>gslice_array (Clase)
Clase de plantilla auxiliar e interna que admite objetos de segmentos generales proporcionando operaciones entre matrices de subconjuntos definidas por el segmento general de una valarray.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Type>  
class gslice_array : public gsplice {  
public:  
    typedef Type value_type;  
    void operator=(const valarray<Type>& x) const;

 
 
    void operator=(const Type& x) const;

 
 
    void operator*=(const valarray<Type>& x) const;

 
 
    void operator/=(const valarray<Type>& x) const;

 
 
    void operator%=(const valarray<Type>& x) const;

 
 
    void operator+=(const valarray<Type>& x) const;

 
 
    void operator-=(const valarray<Type>& x) const;

 
 
    void operator^=(const valarray<Type>& x) const;

 
 
    void operator&=(const valarray<Type>& x) const;

 
 
    void operator|=(const valarray<Type>& x) const;

 
 
    void operator<<=(const valarray<Type>& x) const;

 
 
    void operator>>=(const valarray<Type>& x) const;

 
 
// The rest is private or implementation defined  
}  
```  
  
## <a name="remarks"></a>Comentarios  
 La clase describe un objeto que almacena una referencia a un objeto **va** de la clase [valarray](../standard-library/valarray-class.md)**\<Type>**, junto con un objeto **gs** de la clase [gslice](../standard-library/gslice-class.md), que describe la secuencia de los elementos que se pueden seleccionar desde el objeto **valarray\<Type>**.  
  
 Para construir un objeto **gslice_array\<Type>**, se escribe solo una expresión de formato [va&#91;gs&#93;](../standard-library/valarray-class.md#op_at). Las funciones miembro de la clase gslice_array se comportarán como las signaturas de función correspondientes definidas para **valarray\<Type>**, excepto en que solo la secuencia de elementos seleccionados se ve afectada.  
  
 La clase de plantilla se crea indirectamente por determinadas operaciones valarray y no se puede usar directamente en el programa. En su lugar, el operador de subíndice de segmento usa una clase de plantilla auxiliar interna:  
  
 `gslice_array`\< **Type**> `valarray`\< **Type**>:: `operator[]` ( **constgslice&**).  
  
 Para construir un objeto **gslice_array\<Type>**, se escribe solo una expresión de formato **va[gsl]**, para un segmento **gsl** de valarray **va**. Las funciones miembro de la clase gslice_array se comportarán como las signaturas de función correspondientes definidas para **valarray\<Type>**, excepto en que solo la secuencia de elementos seleccionados se ve afectada. La secuencia controlada por gslice_array se define mediante los tres parámetros del constructor de segmento, el índice del primer elemento en el primer segmento, el número de elementos en cada segmento y la distancia entre los elementos de cada segmento.  
  
 En el ejemplo siguiente:  
  
```  
const size_t lv[] = {2, 3};  
const size_t dv[] = {7, 2};  
const valarray<size_t> len(lv, 2), str(dv, 2);

// va[gslice(3, len, str)] selects elements with  
//   indices 3, 5, 7, 10, 12, 14  
```  
  
 Los índices deben ser válidos para que el procedimiento sea válido.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [gslice::gslice](../standard-library/gslice-class.md#gslice) para obtener un ejemplo de cómo declarar y usar una slice_array.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<valarray>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

