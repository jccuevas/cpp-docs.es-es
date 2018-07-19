---
title: Restricciones de tipo genérico parámetros (C++ / CLI) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- where
dev_langs:
- C++
helpviewer_keywords:
- where keyword [C++]
- constraints, C++
ms.assetid: eb828cc9-684f-48a3-a898-b327700c0a63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c9787eb87ab701d067762a436d92b2fba3fabcbb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883347"
---
# <a name="constraints-on-generic-type-parameters-ccli"></a>Restricciones de parámetros de tipo genérico (C++/CLI)
En las declaraciones de método o tipo genérico, puede calificar un parámetro de tipo con restricciones. Una restricción es un requisito que deben satisfacer los tipos utilizados como argumentos de tipo. Por ejemplo, una restricción puede ser que el argumento de tipo debe implementar una determinada interfaz o heredar de una clase específica.  
  
 Las restricciones son opcionales; no se especifica una restricción en un parámetro es equivalente a restringir ese parámetro para <xref:System.Object>.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
where type-parameter: constraint list  
```  
  
#### <a name="parameters"></a>Parámetros  
 *parámetro de tipo*  
 Uno de los parámetros de tipo, que se restringirá.  
  
 *lista de restricciones*  
 *lista de restricciones* es una lista separada por comas de las especificaciones de restricción. La lista puede incluir interfaces que implementará mediante el parámetro de tipo.  
  
 La lista puede incluir también una clase. Para el argumento de tipo satisfacer una restricción de clase base, debe ser la misma clase que la restricción o derivan de la restricción.  
  
 También puede especificar `gcnew()` para indicar el argumento de tipo debe tener un constructor sin parámetros público; o `ref class` para indicar el argumento de tipo debe ser un tipo de referencia, incluido cualquier clase, una interfaz, un delegado o un tipo de matriz; o `value class` a indicar que el argumento de tipo debe ser un tipo de valor. Cualquier valor de tipo excepto Nullable\<T > se puede especificar.  
  
 También puede especificar un parámetro genérico como una restricción. El argumento de tipo proporcionado para el tipo que se restringen debe ser o derivar del tipo de la restricción. Esto se denomina una restricción de tipo naked.  
  
## <a name="remarks"></a>Comentarios  
 La cláusula de restricción se compone de **donde** seguido de un parámetro de tipo, dos puntos (**:**) y la restricción, que especifica la naturaleza de la restricción en el parámetro de tipo. **donde** es una palabra clave contextual; vea [palabras clave contextuales](../windows/context-sensitive-keywords-cpp-component-extensions.md) para obtener más información. Separe varios **donde** cláusulas con un espacio.  
  
 Las restricciones se aplican al tipo de parámetros que se pondrán limitaciones en los tipos que pueden usarse como argumentos para un tipo o método genérico.  
  
 Restricciones de clase y de interfaz especifican que los tipos de argumento deben ser o heredar de una clase especificada o implementar una interfaz especificada.  
  
 La aplicación de restricciones a un método o tipo genérico permite que el código de ese tipo o método para aprovechar las ventajas de las conocidas características de los tipos restringidas. Por ejemplo, puede declarar una clase genérica de forma que el parámetro de tipo implementa la **IComparable\<T >** interfaz:  
  
```  
// generics_constraints_1.cpp  
// compile with: /c /clr  
using namespace System;  
generic <typename T>  
where T : IComparable<T>  
ref class List {};  
```  
  
 Esta restricción requiere que un argumento de tipo para `T` implementa `IComparable<T>` en tiempo de compilación. También permite que los métodos de interfaz, como **CompareTo**, que se llame a. No se necesita ninguna conversión de tipos en una instancia del parámetro de tipo para llamar a métodos de interfaz.  
  
 Los métodos estáticos de clase de argumento de tipo no se puede llamar a través del parámetro de tipo; se pueden llamar solo a través de los tipos con nombre real.  
  
 Una restricción no puede ser un tipo de valor, incluidos tipos integrados como `int` o **doble**. Puesto que los tipos de valor no pueden tener clases derivadas, sólo una clase nunca sería puede satisfacer la restricción. En ese caso, se puede reescribir la interfaz genérica con el parámetro de tipo que se sustituye por el tipo de valor específico.  
  
 Las restricciones son necesarias en algunos casos ya que el compilador no permite el uso de métodos u otras características de un tipo desconocido, a menos que las restricciones implican que el tipo desconocido es compatible con los métodos o interfaces.  
  
 Se pueden especificar varias restricciones para el mismo parámetro de tipo en una lista separada por comas  
  
```  
// generics_constraints_2.cpp  
// compile with: /c /clr  
using namespace System;  
using namespace System::Collections::Generic;  
generic <typename T>  
where T : List<T>, IComparable<T>  
ref class List {};  
```  
  
 Con varios parámetros de tipo, utilice uno **donde** cláusula para cada parámetro de tipo. Por ejemplo:  
  
```  
// generics_constraints_3.cpp  
// compile with: /c /clr  
using namespace System;  
using namespace System::Collections::Generic;  
  
generic <typename K, typename V>  
   where K: IComparable<K>  
   where V: IComparable<K>  
ref class Dictionary {};  
```  
  
 En resumen, utilice las restricciones en el código según las reglas siguientes:  
  
-   Si se enumeran varias restricciones, las restricciones pueden aparecer en cualquier orden.  
  
-   Las restricciones también pueden ser tipos de clase, como clases base abstractas. Sin embargo, no pueden ser las restricciones de tipos de valor o clases selladas.  
  
-   Las restricciones no pueden ser propios parámetros de tipo, pero pueden incluir los parámetros de tipo en un tipo construido abierto. Por ejemplo:  
  
    ```  
    // generics_constraints_4.cpp  
    // compile with: /c /clr  
    generic <typename T>  
    ref class G1 {};  
  
    generic <typename Type1, typename Type2>  
    where Type1 : G1<Type2>   // OK, G1 takes one type parameter  
    ref class G2{};  
    ```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar restricciones para llamar a métodos de instancia en parámetros de tipo.  
  
```  
// generics_constraints_5.cpp  
// compile with: /clr  
using namespace System;  
  
interface class IAge {  
   int Age();  
};  
  
ref class MyClass {  
public:  
   generic <class ItemType> where ItemType : IAge   
   bool isSenior(ItemType item) {  
      // Because of the constraint,  
      // the Age method can be called on ItemType.  
      if (item->Age() >= 65)   
         return true;  
      else  
         return false;  
   }  
};  
  
ref class Senior : IAge {  
public:  
   virtual int Age() {  
      return 70;  
   }  
};  
  
ref class Adult: IAge {  
public:  
   virtual int Age() {  
      return 30;  
   }  
};  
  
int main() {  
   MyClass^ ageGuess = gcnew MyClass();  
   Adult^ parent = gcnew Adult();  
   Senior^ grandfather = gcnew Senior();  
  
   if (ageGuess->isSenior<Adult^>(parent))  
      Console::WriteLine("\"parent\" is a senior");  
   else  
      Console::WriteLine("\"parent\" is not a senior");  
  
   if (ageGuess->isSenior<Senior^>(grandfather))  
      Console::WriteLine("\"grandfather\" is a senior");  
   else  
      Console::WriteLine("\"grandfather\" is not a senior");  
}  
```  
  
```Output  
"parent" is not a senior  
"grandfather" is a senior  
```  
  
## <a name="example"></a>Ejemplo  
 Cuando se usa un parámetro de tipo genérico como una restricción, se denomina una restricción de tipo naked. Restricciones de tipo naked son útiles cuando una función miembro con su propio parámetro de tipo debe restringir ese parámetro para el parámetro de tipo del tipo contenedor.  
  
 En el ejemplo siguiente, T es una restricción de tipo naked en el contexto del método Add.  
  
 Restricciones de tipo naked también pueden usarse en definiciones de clase genéricas. La utilidad de las restricciones de tipo naked con clases genéricas está limitada porque el compilador puede suponer nada acerca de una restricción de tipo naked excepto que se derive de <xref:System.Object>. Utilizar restricciones de tipo naked en clases genéricas en escenarios en los que desea aplicar una relación de herencia entre dos parámetros de tipo.  
  
```  
// generics_constraints_6.cpp  
// compile with: /clr /c  
generic <class T>  
ref struct List {  
   generic <class U>  
   where U : T  
   void Add(List<U> items)  {}  
};  
  
generic <class A, class B, class C>  
where A : C  
ref struct SampleClass {};  
```  
  
## <a name="see-also"></a>Vea también  
 [Genéricos](../windows/generics-cpp-component-extensions.md)