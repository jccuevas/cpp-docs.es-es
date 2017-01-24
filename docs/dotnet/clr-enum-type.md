---
title: "Tipo de enumeraci&#243;n de CLR | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "enum y class (palabras clave) [C++]"
  - "enum y struct (palabras clave) [C++]"
  - "ámbito, de enumeración de CLR"
ms.assetid: 4541d952-97bb-4e35-a7f8-d14f5f6a6606
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tipo de enumeraci&#243;n de CLR
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Ha cambiado la declaración y el comportamiento de las enumeraciones de Extensiones administradas para C\+\+ a [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  
  
 La palabra clave `__value` precede a la declaración de la enumeración en Extensiones administradas.  La idea es distinguir la enumeración nativa de la enumeración de CLR que se deriva de `System::ValueType`, a la vez que sugerir una funcionalidad análoga.  Por ejemplo:  
  
```  
__value enum e1 { fail, pass };  
public __value enum e2 : unsigned short  {   
   not_ok = 1024,   
   maybe, ok = 2048   
};  
```  
  
 La nueva sintaxis resuelve el problema de distinguir enumeraciones nativas y de CLR resaltando la naturaleza de la clase de ésta última en lugar de sus raíces de tipo de valor.  Como tal, se descarta la palabra clave `__value`, reemplazada por el par de palabras clave espaciadas de `enum class`.  Esto proporciona una simetría de palabras clave emparejadas a las declaraciones de las clases de referencia, de valor y de interfaz:  
  
```  
enum class ec;  
value class vc;  
ref class rc;  
interface class ic;  
```  
  
 La traducción del par de enumeración `e1` y `e2` en la nueva sintaxis se parece a lo siguiente:  
  
```  
enum class e1 { fail, pass };  
public enum class e2 : unsigned short {   
   not_ok = 1024,  
   maybe, ok = 2048   
};  
```  
  
 Aparte de este pequeño cambio sintáctico, el comportamiento del tipo de enumeración CLR ha cambiado en muchos aspectos:  
  
-   Ya no se admite una declaración adelantada de una enumeración CLR.  No hay asignación.  Simplemente se marca como un error de tiempo de compilación.  
  
```  
__value enum status; // Managed Extensions: ok  
enum class status;   // new syntax: error  
```  
  
-   Se ha invertido la resolución de sobrecarga entre los tipos aritméticos integrados y la jerarquía de clases `Object` entre las dos versiones del lenguaje.  Como efecto secundario, las enumeraciones CLR ya no se convierten implícitamente en tipos aritméticos.  
  
-   En la nueva sintaxis, una enumeración CLR mantiene su propio ámbito, que no es el caso en Extensiones administradas.  Antes, los enumeradores estaban visibles dentro del ámbito contenedor de la enumeración.  Ahora, los enumeradores se encapsulan dentro del ámbito de la enumeración.  
  
## Las enumeraciones de CLR son un tipo de objeto  
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
  
 Para el programador de C\+\+ nativo, la respuesta natural a la pregunta de qué instancia de `f()` sobrecargado se invoca es la de `f(int)`.  Una enumeración es una constante entera simbólica y participa en las promociones enteras estándar que tienen prioridad en este caso.  De hecho, en Extensiones administradas ésta era la instancia en la que se resolvía la llamada.  Esto provocaba algunas sorpresas, no cuando se utilizaban pensando en un marco de C\+\+ nativo, sino cuando se necesitaban para interactuar con el marco de trabajo de la biblioteca de clases base BCL\(Base Class Library\) existente, donde `Enum` es una clase derivada indirectamente de `Object`.  En el diseño del lenguaje [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)], la instancia de `f()` invocada es la de `f(Object^)`.  
  
 La manera en que [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)] ha decidido aplicar esto es no admitir conversiones implícitas entre un tipo de enumeración de CLR y los tipos aritméticos.  Esto significa que cualquier asignación de un objeto de un tipo de enumeración de CLR a un tipo aritmético requerirá una conversión de tipos explícita.  Por ejemplo, teniendo  
  
```  
void f( int );  
```  
  
 como método no sobrecargado, en Extensiones administradas, la llamada  
  
```  
f( rslt ); // ok: Managed Extensions; error: new syntax  
```  
  
 es correcta y el valor contenido dentro de `rslt` se convierte implícitamente en un valor entero.  En [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)], esta llamada no se compila.  Para traducirla correctamente, se debe insertar un operador de conversión:  
  
```  
f( safe_cast<int>( rslt )); // ok: new syntax  
```  
  
## Ámbito del tipo de enumeración de CLR  
 Uno de los cambios entre los lenguajes C y C\+\+ era la adición en C\+\+ de ámbito dentro de la utilidad del struct.  En C, un struct es simplemente un agregado de datos sin compatibilidad de una interfaz o de un ámbito asociado.  Esto supuso realmente un cambio radical en aquel momento y fue un tema polémico para muchos nuevos usuarios de C\+\+ que venían del lenguaje C.  La relación entre la enumeración nativa y la enumeración de CLR es análoga.  
  
 En Extensiones administradas, se hizo un intento de definir nombres insertados de forma poco rigurosa para los enumeradores de una enumeración de CLR a fin de simular la ausencia de ámbito dentro de la enumeración nativa.  Esto no dio un buen resultado.  El problema es que esto hace que los enumeradores se desborden al espacio de nombres global, lo que dificulta la administración de las colisiones de nombres.  En la nueva sintaxis, nos hemos ajustado a los demás lenguajes de CLR para lograr la compatibilidad con ámbitos dentro de la enumeración de CLR.  
  
 Esto significa que la nueva sintaxis no reconocerá ningún uso incompleto de un enumerador de una enumeración de CLR.  Examinemos un ejemplo real.  
  
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
  
      // here are the problems …  
      optionList->Add(S"?", __box(OPTION_USAGE)); // (1)  
      optionList->Add(S"help", __box(OPTION_USAGE)); // (2)  
  
      itagList = new ListDictionary;  
      itagList->Add(S"returns",   
         __box(XDC0004_WRN_XML_LOAD_FAILURE)); // (3)  
   }  
};  
```  
  
 Cada uno de los tres usos incompletos de los nombres de enumeradores \(`(1)`, `(2)` y `(3)`\) necesitará completarse en la traducción a la nueva sintaxis para que el código fuente se pueda compilar.  Ésta es una traducción correcta del código fuente original:  
  
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
  
 Esto cambia la estrategia de diseño entre una enumeración nativa y una enumeración de CLR.  Con una enumeración de CLR que mantiene un ámbito asociado en [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)], no es necesario ni eficaz encapsular la declaración de la enumeración en una clase.  Esta expresión evolucionó en torno a la época de cfront 2.0 en Bell Laboratories también para resolver el problema de contaminación de nombres globales.  
  
 En la versión beta original de la nueva biblioteca iostream de Jerry Schwarz en Bell Laboratories, Jerry no encapsuló las enumeraciones asociadas definidas para la biblioteca y los enumeradores comunes como `read`, `write`, `append`, etc., hacían casi imposible que los usuarios compilaran el código existente.  Una solución hubiera sido alterar los nombres, como `io_read`, `io_write`, etc. Otra solución hubiera sido modificar el lenguaje agregando el ámbito a una enumeración, pero esto no era posible en aquella época.  La solución intermedia fue encapsular la enumeración dentro de una clase o una jerarquía de clases, en las que el nombre de etiqueta y los enumeradores de la enumeración rellenaban el ámbito de la clase que la incluía\) Es decir, la motivación para incluir las enumeraciones dentro de clases, al menos originalmente, no fue una respuesta filosófica sino práctica al problema de la contaminación de los espacios de nombres globales.  
  
 Con la enumeración de [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)], ya no hay ninguna ventaja convincente para encapsular una enumeración dentro de una clase.  De hecho, si examina los espacios de nombres `System`, verá que las enumeraciones, clases e interfaces habitan todas en el mismo espacio de la declaración.  
  
## Vea también  
 [Tipos de valor y su comportamiento \(C\+\+\/CLI\)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [enum class](../windows/enum-class-cpp-component-extensions.md)