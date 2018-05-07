---
title: Tipo de enumeración CLR | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scope, of CLR enum
- enum struct keyword [C++]
- enum class keyword [C++]
ms.assetid: 4541d952-97bb-4e35-a7f8-d14f5f6a6606
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2416a306373db08c5e925b4987fc8a9273973c39
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="clr-enum-type"></a>Tipo de enumeración de CLR
Ha cambiado la declaración y el comportamiento de las enumeraciones de extensiones administradas para C++ a Visual C++.  
  
 La declaración de enumeración de extensiones administradas está precedida por el `__value` (palabra clave). La idea es distinguir la enumeración nativa de la enumeración CLR que se deriva de `System::ValueType`, mientras lo que sugiere una funcionalidad similar. Por ejemplo:  
  
```  
__value enum e1 { fail, pass };  
public __value enum e2 : unsigned short  {   
   not_ok = 1024,   
   maybe, ok = 2048   
};  
```  
  
 La nueva sintaxis resuelve los problemas de distinción nativo y las enumeraciones CLR resaltando la naturaleza de la clase de este último en lugar de sus raíces de tipo de valor. Por lo tanto, la `__value` palabra clave se descarta y se reemplazan por los pares de palabra clave espaciadas de `enum class`. Esto proporciona una simetría de palabras clave emparejadas a las declaraciones de las clases de interfaz, el valor y la referencia:  
  
```  
enum class ec;  
value class vc;  
ref class rc;  
interface class ic;  
```  
  
 La traducción del par de enumeración `e1` y `e2` en la nueva sintaxis tiene el siguiente aspecto:  
  
```  
enum class e1 { fail, pass };  
public enum class e2 : unsigned short {   
   not_ok = 1024,  
   maybe, ok = 2048   
};  
```  
  
 Aparte de este pequeño cambio sintáctico, el comportamiento del tipo de enumeración CLR se ha cambiado en una de varias maneras:  
  
-   Ya no se admite una declaración adelantada de una enumeración CLR. No hay ninguna asignación. Simplemente se indica como un error en tiempo de compilación.  
  
```  
__value enum status; // Managed Extensions: ok  
enum class status;   // new syntax: error  
```  
  
-   La resolución de sobrecarga entre los tipos aritméticos integrados y `Object` jerarquía de clases se ha invertido entre las dos versiones del lenguaje. Como efecto secundario, las enumeraciones CLR ya no es implícitamente se convierten en tipos aritméticos.  
  
-   En la nueva sintaxis, una enumeración de CLR mantiene su propio ámbito, que no es el caso en extensiones administradas. Anteriormente, los enumeradores estaban visibles dentro del ámbito contenedor de la enumeración. Ahora, los enumeradores se encapsulan dentro del ámbito de la enumeración.  
  
## <a name="clr-enums-are-a-kind-of-object"></a>Las enumeraciones de CLR son un tipo de objeto  
 Observe el fragmento de código siguiente:  
  
```  
__value enum status { fail, pass };  
  
void f( Object* ){ Console::WriteLine("f(Object)\n"); }  
void f( int ){ Console::WriteLine("f(int)\n"); }  
  
int main()  
{  
   status rslt = fail;  
  
   f( rslt ); // which f is invoked?  
}  
```  
  
 Para los programadores de C++ nativo, natural de respuesta a la pregunta de qué instancia de sobrecargado `f()` se invoca es la de `f(int)`. Una enumeración es una constante entera simbólica y participa en las promociones enteras estándar que tienen prioridad en este caso.  Y, de hecho en extensiones administradas era la instancia a la que se resuelve la llamada. Esto provocaba algunas sorpresas - no cuando se usa en una cuenta de of de marco de C++ nativo - pero cuando se necesitaban para interactuar con el marco de trabajo existente de BCL (biblioteca de clases Base), donde un `Enum` es una clase derivada indirectamente de `Object`. En el diseño del lenguaje Visual C++, la instancia de `f()` invoca es el de `f(Object^)`.  
  
 La manera en que Visual C++ ha decidido aplicar esto es no admitir conversiones implícitas entre un tipo de enumeración CLR y los tipos aritméticos. Esto significa que cualquier asignación de un objeto de un tipo de enumeración CLR a un tipo aritmético requerirá una conversión explícita. Por lo tanto, por ejemplo, dada  
  
```  
void f( int );  
```  
  
 como un método no sobrecargado, en extensiones administradas, la llamada  
  
```  
f( rslt ); // ok: Managed Extensions; error: new syntax  
```  
  
 es Aceptar y el valor dentro de `rslt` se convierte implícitamente en un valor entero. En Visual C++, esta llamada produce un error de compilación. Para convertirlo correctamente, se debe insertar un operador de conversión:  
  
```  
f( safe_cast<int>( rslt )); // ok: new syntax  
```  
  
## <a name="the-scope-of-the-clr-enum-type"></a>El ámbito del tipo de enumeración CLR  
 Uno de los cambios entre los lenguajes C y C++ era la adición en C++ de ámbito dentro de la utilidad del struct. En C, un struct es simplemente un agregado de datos sin compatibilidad de una interfaz o un ámbito asociado. Esto era bastante un cambio radical en el momento y era un problema para muchos nuevos usuarios de C++ procedentes de lenguaje C conflictivas. La relación entre la enumeración nativa y enumeración de CLR es análoga.  
  
 En extensiones administradas, se realizó un intento para definir nombres débilmente insertados para los enumeradores de una enumeración CLR con el fin de simular la ausencia de ámbito dentro de la enumeración nativa. Esto no fue correcta. El problema es que esto hace que los enumeradores se desborden el espacio de nombres global, lo que dificulta la administrar conflictos de nombres. En la nueva sintaxis, nos hemos ajustado a los demás idiomas CLR en la compatibilidad con ámbitos dentro de la enumeración CLR.  
  
 Esto significa que cualquier uso no calificado de un enumerador de una enumeración CLR no reconocerá la nueva sintaxis. Veamos un ejemplo del mundo real.  
  
```  
// Managed Extensions supporting weak injection  
__gc class XDCMake {  
public:  
   __value enum _recognizerEnum {   
      UNDEFINED,  
      OPTION_USAGE,   
      XDC0001_ERR_PATH_DOES_NOT_EXIST = 1,  
      XDC0002_ERR_CANNOT_WRITE_TO = 2,  
      XDC0003_ERR_INCLUDE_TAGS_NOT_SUPPORTED = 3,  
      XDC0004_WRN_XML_LOAD_FAILURE = 4,  
      XDC0006_WRN_NONEXISTENT_FILES = 6,  
   };  
  
   ListDictionary* optionList;  
   ListDictionary* itagList;  
  
   XDCMake() {  
      optionList = new ListDictionary;  
  
      // here are the problems...  
      optionList->Add(S"?", __box(OPTION_USAGE)); // (1)  
      optionList->Add(S"help", __box(OPTION_USAGE)); // (2)  
  
      itagList = new ListDictionary;  
      itagList->Add(S"returns",   
         __box(XDC0004_WRN_XML_LOAD_FAILURE)); // (3)  
   }  
};  
```  
  
 Cada uno de los tres no calificados usos de los nombres de enumeradores (`(1)`, `(2)`, y `(3)`) será necesario que estén calificados en la conversión a la nueva sintaxis en orden para poder compilar el código de origen. Esta es una traducción correcta del código fuente original:  
  
```  
ref class XDCMake {  
public:  
   enum class _recognizerEnum {  
      UNDEFINED, OPTION_USAGE,   
      XDC0001_ERR_PATH_DOES_NOT_EXIST = 1,  
      XDC0002_ERR_CANNOT_WRITE_TO = 2,  
      XDC0003_ERR_INCLUDE_TAGS_NOT_SUPPORTED = 3,  
      XDC0004_WRN_XML_LOAD_FAILURE = 4,  
      XDC0006_WRN_NONEXISTENT_FILES = 6  
   };  
  
   ListDictionary^ optionList;  
   ListDictionary^ itagList;  
  
   XDCMake() {  
      optionList = gcnew ListDictionary;  
      optionList->Add("?",_recognizerEnum::OPTION_USAGE); // (1)  
      optionList->Add("help",_recognizerEnum::OPTION_USAGE); //(2)  
      itagList = gcnew ListDictionary;  
      itagList->Add( "returns",   
         _recognizerEnum::XDC0004_WRN_XML_LOAD_FAILURE); //(3)  
   }  
};  
```  
  
 Esto cambia la estrategia de diseño entre nativo y una enumeración de CLR. Con una enumeración CLR mantiene un ámbito asociado en Visual C++, es necesario ni eficaz encapsular la declaración de la enumeración en una clase. Esta expresión evolucionó en torno a la época de cfront 2.0 en Bell Laboratories también para resolver el problema de corrupción de nombres global.  
  
 En la versión beta original de la nueva biblioteca iostream Jerry Schwarz en Bell Laboratories, Juan no encapsula todos los las enumeraciones asociadas definidas para la biblioteca y los enumeradores comunes como `read`, `write`, `append`, etc. , hacían casi imposible que los usuarios compilar el código existente. Una solución hubiera sido trastocar los nombres, como `io_read`, `io_write`, etcetera. Una segunda solución hubiera sido modificar el lenguaje agregando ámbito a una enumeración, pero esto no era posible en el momento. La solución intermedia fue encapsular la enumeración dentro de la clase, o jerarquía de clases, donde el nombre de etiqueta y los enumeradores de la enumeración rellenan el ámbito de la clase envolvente.) Es decir, la motivación para incluir las enumeraciones dentro de clases, al menos originalmente, no estaba filosófica, pero una respuesta resulta muy práctica para el problema de corrupción de espacio de nombres global.  
  
 Con la enumeración de Visual C++, ya no hay ninguna ventaja convincente para encapsular una enumeración dentro de una clase. De hecho, si observa la `System` espacios de nombres, verá que las enumeraciones, clases e interfaces todos ocupan el mismo espacio de declaración.  
  
## <a name="see-also"></a>Vea también  
 [Tipos de valor y sus comportamientos (C++ / CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [clase de enumeración](../windows/enum-class-cpp-component-extensions.md)