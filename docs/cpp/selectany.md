---
title: selectany | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- selectany_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], selectany
- selectany __declspec keyword
ms.assetid: 9c353017-5a42-4f50-b741-bd13da1ce84d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8d8b4a1a78fb8231d407e60ded2c6dea3f7c891d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="selectany"></a>selectany
**Específicos de Microsoft**  
  
 Indica al compilador que el elemento de datos globales declarado (variable u objeto) es un COMDAT de selección (una función empaquetada).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__declspec( selectany ) declarator  
```  
  
## <a name="remarks"></a>Comentarios  
 En tiempo de vinculación, si se ven varias definiciones de un COMDAT, el vinculador selecciona una y descarta el resto. Si la opción del vinculador [/OPT: ref](../build/reference/opt-optimizations.md) (optimizaciones) está seleccionado, a continuación, se producirá la eliminación de COMDAT quitar todos los elementos de los datos en la salida del vinculador.  
  
 Los constructores y la asignación mediante una función global o métodos estáticos en la declaración no crean una referencia y no impedirán la eliminación de /OPT:REF. No se debe depender de los efectos secundarios de ese código si no existen otras referencias a los datos.  
  
 Para los objetos globales inicializados dinámicamente, `selectany` también descartará un código de inicialización de objeto no referenciado.  
  
 Un elemento de datos globales se puede inicializar normalmente solo una vez en un proyecto EXE o DLL. `selectany` se puede utilizar en la inicialización de datos globales definidos por los encabezados cuando el mismo encabezado aparece en más de un archivo de código fuente. `selectany` está disponible en los compiladores de C y C++.  
  
> [!NOTE]
>  `selectany` solo se puede aplicar a la inicialización real de elementos de datos globales externamente visibles.  
  
## <a name="example"></a>Ejemplo  
 En este código se muestra cómo usar el atributo `selectany`.  
  
```  
//Correct - x1 is initialized and externally visible   
__declspec(selectany) int x1=1;  
  
//Incorrect - const is by default static in C++, so   
//x2 is not visible externally (This is OK in C, since  
//const is not by default static in C)  
const __declspec(selectany) int x2 =2;  
  
//Correct - x3 is extern const, so externally visible  
extern const __declspec(selectany) int x3=3;  
  
//Correct - x4 is extern const, so it is externally visible  
extern const int x4;  
const __declspec(selectany) int x4=4;  
  
//Incorrect - __declspec(selectany) is applied to the uninitialized  
//declaration of x5  
extern __declspec(selectany) int x5;  
  
// OK: dynamic initialization of global object  
class X {  
public:  
X(int i){i++;};  
int i;  
};  
  
__declspec(selectany) X x(1);  
```  
  
## <a name="example"></a>Ejemplo  
 Este código muestra cómo utilizar el `selectany` atributo para garantizar el plegamiento de COMDAT de datos cuando también se utiliza la [/OPT: ICF](../build/reference/opt-optimizations.md) opción del vinculador. Tenga en cuenta que los datos se deben marcar con `selectany` y se coloca en un **const** sección (solo lectura). Debe especificar explícitamente la sección de solo lectura.  
  
```  
// selectany2.cpp  
// in the following lines, const marks the variables as read only  
__declspec(selectany) extern const int ix = 5;  
__declspec(selectany) extern const int jx = 5;  
int main() {  
   int ij;  
   ij = ix + jx;  
}  
```  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [__declspec](../cpp/declspec.md)   
 [Palabras clave](../cpp/keywords-cpp.md)