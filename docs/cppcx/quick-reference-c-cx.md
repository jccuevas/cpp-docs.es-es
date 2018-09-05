---
title: Referencia rápida (C++ / c++ / CX) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: ba457195-26e5-43aa-b99d-24a871e550f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 272921d0a9ac00ec5ee69fb50a17a34e257b1725
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43692593"
---
# <a name="quick-reference-ccx"></a>Referencia rápida (C++/CX)
El tiempo de ejecución de Windows es compatible con aplicaciones de plataforma Universal de Windows (UWP) que se ejecutan únicamente en un entorno de sistema operativo de confianza, utilizan funciones, tipos de datos y dispositivos autorizados y se distribuyen a través de la Microsoft Store. C++ / c++ / CX simplifican la escritura de aplicaciones de Windows en tiempo de ejecución. En este artículo es una referencia rápida; Para obtener documentación más completa, consulte [Type System](../cppcx/type-system-c-cx.md).  
  
 Cuando se compila en la línea de comandos, utilice el **/ZW** opción del compilador para generar una aplicación para UWP o componente en tiempo de ejecución de Windows. Para obtener acceso a las declaraciones de Windows en tiempo de ejecución, que se definen en los archivos de metadatos (.winmd) de Windows en tiempo de ejecución, especifique el `#using` directiva o la **/FU** opción del compilador. Cuando se crea un proyecto para una aplicación para UWP, Visual Studio de forma predeterminada establece estas opciones y agrega las referencias a todas las bibliotecas en tiempo de ejecución de Windows.  
  
## <a name="quick-reference"></a>Referencia rápida  
  
|Concepto|Standard C++|C++/CX|Comentarios|  
|-------------|--------------------|------------------------------------------------------------------|-------------|  
|Tipos fundamentales|Tipos fundamentales de C++.|C++ / c++ / tipos fundamentales de CX que implementan tipos fundamentales que se definen en el tiempo de ejecución de Windows.|El `default` contiene el espacio de nombres de C++ / c++ / CX tipos fundamentales integrados. El compilador asigna implícitamente C + + / tipos fundamentales de CX para tipos de C++ estándar.<br /><br /> El `Platform` familia de espacios de nombres contiene tipos que implementan tipos fundamentales de Windows en tiempo de ejecución.|  
||`bool`|`bool`|Un valor booleano de 8 bits.|  
||`__wchar_t`|`char16`|Un valor no numérico de 16 bits que representa un punto de código Unicode (UTF-16).|  
||`short`<br /><br /> `unsigned short`|`int16`<br /><br /> `uint16`|Entero de 16 bits con signo.<br /><br /> Entero de 16 bits sin signo.|  
||`int`<br /><br /> `unsigned int`|`int`<br /><br /> `uint32`|Entero de 32 bits con signo.<br /><br /> Entero de 32 bits sin signo.|  
||`long long` O bien `__int64`<br /><br /> `unsigned long long`|`int64`<br /><br /> `uint64`|Entero de 64 bits con signo.<br /><br /> Entero de 64 bits sin signo.|  
||`float, double`|`float32, float64`|Un número de punto flotante de 32 bits o 64 bits conforme a IEEE 754.|  
||`enum {}`|`enum class {}`<br /><br /> O bien<br /><br /> `enum struct {}`|Una enumeración de 32 bits.|  
||(No procede)|`Platform::Guid`|Un valor no numérico de 128 bits (GUID) en el espacio de nombres `Platform` .|  
||`std::time_get`|`Windows::Foundation::DateTime`|Una estructura de fecha y hora.|  
||(No procede)|`Windows::Foundation::TimeSpan`|Una estructura de intervalo de tiempo.|  
||(No procede)|`Platform::Object^`|El objeto base con recuento de referencias en la vista de C++ del sistema de tipos en tiempo de ejecución de Windows.|  
||`std::wstring`<br /><br /> `L"..."`|`Platform::String^`|`Platform::String^` es una secuencia inmutable con recuento de referencias de caracteres Unicode que representan texto.|  
|Puntero|Puntero a objeto (`*`):<br /><br /> `std::shared_ptr`|Identificador-a-objeto (`^`, pronunciado “sombrero”):<br /><br /> *Identificador T^*|Todas las clases de Windows en tiempo de ejecución se declaran con el modificador "identificador a objeto". Se obtiene acceso a los miembros del objeto mediante el operador de acceso de miembro de clase flecha (`->`).<br /><br /> El modificador de hat significa "puntero a un objeto en tiempo de ejecución de Windows que es automáticamente referencia contada." Más concretamente, el "identificador a objeto" declara que el compilador debe insertar código para administrar automáticamente el recuento de referencias del objeto y eliminar el objeto si el recuento de referencias llega a cero.|  
|Referencia|Referencia a un objeto (`&`):<br /><br /> *T* `&` *identifier*|Referencia de seguimiento (`%`):<br /><br /> *T* `%` *identifier*|Modificador de hacer referencia a solo en tiempo de ejecución de Windows se pueden declarar tipos utilizando el seguimiento. Se obtiene acceso a los miembros del objeto mediante el operador de acceso de miembro de clase punto (`.`).<br /><br /> La referencia de seguimiento significa "una referencia a un objeto de tiempo de ejecución de Windows que automáticamente se cuentan las referencias". Más concretamente, una referencia de seguimiento declara que el compilador debe insertar código para administrar automáticamente el recuento de referencias del objeto y eliminar el objeto si el recuento de referencias llega a cero.|  
|declaración de tipos dinámica|`new`|`ref new`|Asigna un objeto en tiempo de ejecución de Windows y, a continuación, devuelve un identificador a ese objeto.|  
|administración de vigencia de objeto|`delete` *identifier*<br /><br /> `delete[]`  *identifier*|(Invoca el destructor).|La vigencia la determina el recuento de referencias. Una llamada para eliminar llama al destructor pero en sí no libera memoria.|  
|declaración de matriz|*Identificador T* `[]`<br /><br /> `std::array` *identifier*|`Array<` *T* `^>^` *identifier* `(` *size* `)`<br /><br /> O bien<br /><br /> `WriteOnlyArray<` *T* `^>`  *identifier* `(` *size* `)`|Declara una matriz de solo escritura modificable unidimensional de tipo T^. La matriz en sí también es un objeto con recuento de referencias que se debe declarar mediante el modificador "identificador a objeto".<br /><br /> Las declaraciones de matriz utilizan una clase de encabezado de plantilla que se encuentra en el espacio de nombres `Platform` .|  
|declaración de clase|`class`  *identifier* `{}`<br /><br /> `struct` *identifier* `{}`|`ref class` *identifier* `{}`<br /><br /> `ref struct` *identifier* `{}`|Declara una clase en tiempo de ejecución que tiene accesibilidad privada predeterminada.<br /><br /> Declara una clase en tiempo de ejecución que tiene accesibilidad pública predeterminada.|  
|declaración de estructura|`struct` *identifier* `{}`<br /><br /> (es decir, una estructura Plain Old Data (POD))|`value class` *identifier* `{}`<br /><br /> `value struct` *identifier* `{}`|Declara un struct de POD que tiene accesibilidad privada predeterminada.<br /><br /> Una clase de valor se puede representar en metadatos de Windows, pero una clase de C++ estándar no se puede.<br /><br /> Declara un struct de POD que tiene accesibilidad pública predeterminada.<br /><br /> Un struct de valor se puede representar en metadatos de Windows, pero un struct de C++ estándar no se puede.|  
|declaración de interfaz|clase abstracta que solo contiene funciones virtuales puras.|`interface class` *identifier* `{}`<br /><br /> `interface struct` *identifier* `{}`|Declara una interfaz que tiene accesibilidad privada predeterminada.<br /><br /> Declara una interfaz que tiene accesibilidad pública predeterminada.|  
|delegado|`std::function`|`public delegate` *tipo de valor devuelto* *delegate-type-identifier* `(` *[parámetros]* `);`|Declara un objeto que se puede invocar como una llamada de función.|  
|evento|(No procede)|`event` *delegate-type-identifier* *event-identifier* `;`<br /><br /> *delegate-type-identifier* *delegate-identifier* = `ref new`*delegate-type-identifier*`( this`*[, parámetros]*`);`<br /><br /> *event-identifier* `+=` *delegate-identifier* `;`<br /><br /> O bien<br /><br /> `EventRegistrationToken` *token-identifier* = *obj*`.`*event-identifier*`+=`*delegate-identifier*`;`<br /><br /> O bien<br /><br /> `auto` *identificador de token* = *obj*. *identificador de evento*`::add(`*identificador del delegado*`);`<br /><br /> *obj* `.` *event-identifier* `-=` *token-identifier* `;`<br /><br /> O bien<br /><br /> *obj* `.` *event-identifier* `::remove(` *token-identifier* `);`|Declare un objeto de evento, que almacena una colección de controladores de eventos (delegados) a los que se llama cuando se produce un evento.<br /><br /> Crear un controlador de eventos.<br /><br /> Agrega un controlador de eventos.<br /><br /> Cuando se agrega un controlador de eventos, se devuelve un token de evento (*token-identifier*). Si vas a quitar explícitamente el controlador de eventos, debes guardar el token de evento para uso posterior.<br /><br /> Quita un controlador de eventos.<br /><br /> Para quitar un controlador de eventos, debes especificar el token de evento que guardaste al agregar el controlador de eventos.|  
|propiedad|(No procede)|`property` *T* *identifier*;<br /><br /> `property` *T* *identifier* `[` *índice* `];`<br /><br /> `property` *T* `default[` *índice* `];`|Declara que se tiene acceso a una función miembro de clase o de objeto mediante la misma sintaxis que se utiliza para tener acceso a un miembro de datos o a un elemento de matriz indizado.<br /><br /> Declara una propiedad en una función miembro de clase o de objeto.<br /><br /> Declara una propiedad indizada en una función miembro de objeto.<br /><br /> Declara una propiedad indizada en una función miembro de clase.|  
|Tipos parametrizados|plantillas|`generic <typename` *T* `> interface class` *identifier* `{}`<br /><br /> `generic <typename` *T* `> delegate` *[return-type]* *delegate-identifier* `() {}`|Declara una clase de interfaz parametrizada.<br /><br /> Declara un delegado parametrizado.|  
|Tipos de valor que aceptan valores NULL|`boost::optional<T>`|[Platform:: ibox \<T >](../cppcx/platform-ibox-interface.md)|Permite a variables de tipos escalares y structs de valor obtener un valor de `nullptr`.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia del lenguaje de Visual C++](../cppcx/visual-c-language-reference-c-cx.md)