---
title: "Punteros inteligentes (C++ moderno) | Microsoft Docs"
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
ms.assetid: 909ef870-904c-49b6-b8cd-e9d0b7dc9435
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Punteros inteligentes (C++ moderno)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En la programación del lenguaje C\+\+ actual, la biblioteca estándar incluye *punteros inteligentes*, que se utilizan para asegurarse de que los programas están libres de memoria y de pérdidas de recursos y son seguros ante excepciones.  
  
## Usos de los punteros inteligentes  
 Los punteros inteligentes se definen en el espacio de nombres `std` del archivo de encabezado [\<memory\>](../standard-library/memory.md).  Son cruciales en la expresión de programación [RAII](../cpp/objects-own-resources-raii.md) o *Resource Acquisition Is Initialialization*.  El objetivo principal de esta expresión es asegurarse de que la adquisición de recursos ocurre al mismo tiempo que se inicializa el objeto, de manera que todos los recursos del objeto se creen y se dispongan en una sola línea de código.  En la práctica, el principio básico RAII consiste en proporcionar la propiedad de cualquier recurso asignado por montón \(por ejemplo, memoria asignada dinámicamente o identificadores de objetos del sistema\) a un objeto asignado a la pila cuyo destructor contiene código para eliminar o liberar el recurso, además de cualquier código asociado de limpieza.  
  
 En la mayoría de los casos, cuando se inicializa un puntero o un identificador de recursos sin formato para apuntar a un recurso real, el puntero se pasa inmediatamente a un puntero inteligente.  En el lenguaje C\+\+ actual, los punteros sin formato se utilizan únicamente en pequeños bloques de código de ámbito limitado, bucles o funciones auxiliares donde el rendimiento es crucial y no hay ninguna posibilidad de confusión sobre la propiedad.  
  
 En el ejemplo siguiente se compara una declaración de puntero sin formato con una declaración de puntero inteligente.  
  
 [!code-cpp[smart_pointers_intro#1](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_1.cpp)]  
  
 Como se muestra en el ejemplo, un puntero inteligente es una plantilla de clase que se declara en la pila y se inicializa con un puntero sin formato que apunta a un objeto asignado por montón.  Una vez que se inicializa el puntero inteligente, se convierte en propietario del puntero sin formato.  Esto significa que el puntero inteligente es responsable de eliminar la memoria que el puntero sin formato especifica.  El destructor del puntero inteligente contiene la llamada de eliminación y, dado que el puntero inteligente se declara en la pila, su destructor se invoca cuando el puntero inteligente sale del ámbito, incluso si se produce una excepción en alguna parte que se encuentre más arriba en la pila.  
  
 Para acceder al puntero encapsulado, utilice los conocidos operadores de puntero `->` y `*`, que la clase del puntero inteligente sobrecarga para devolver el puntero sin formato encapsulado.  
  
 La expresión del puntero inteligente de C\+\+ se asemeja a la creación de objetos en lenguajes como C\#: se crea el objeto y después se permite al sistema que se ocupe de eliminarlo en el momento correcto.  La diferencia es que ningún recolector de elementos no utilizados independiente se ejecuta en segundo plano; la memoria se administra con las reglas estándar de ámbito de C\+\+, de modo que el entorno en tiempo de ejecución es más rápido y eficaz.  
  
> [!IMPORTANT]
>  Cree siempre punteros inteligentes en una línea de código independiente, nunca en una lista de parámetros, para que no se produzca una pérdida de recursos imperceptible debido a algunas reglas de asignación de la lista de parámetros.  
  
 En el ejemplo siguiente se muestra cómo se puede utilizar un tipo de puntero inteligente `unique_ptr` de la biblioteca de plantillas estándar para encapsular un puntero a un objeto grande.  
  
 [!code-cpp[smart_pointers_intro#2](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_2.cpp)]  
  
 En el ejemplo se muestran los pasos básicos siguientes para utilizar punteros inteligentes.  
  
1.  Declare el puntero inteligente como variable automática \(local\). \(No utilice la expresión `new` o `malloc` en el propio puntero inteligente\).  
  
2.  En el parámetro de tipo, especifique el tipo al que apunta el puntero encapsulado.  
  
3.  Pase un puntero sin formato al objeto `new`\-ed en el constructor de puntero inteligente. \(Algunas funciones de utilidad o constructores de puntero inteligente hacen esto por usted.\)  
  
4.  Utilice los operadores sobrecargados `->` y `*` para tener acceso al objeto.  
  
5.  Deje que el puntero inteligente elimine el objeto.  
  
 Los punteros inteligentes están diseñados para ser lo más eficaces posible tanto en términos de memoria como de rendimiento.  Por ejemplo, el único miembro de datos de `unique_ptr` es el puntero encapsulado.  Esto significa que `unique_ptr` tiene exactamente el mismo tamaño que ese puntero, cuatro u ocho bytes.  El acceso al puntero encapsulado a través del puntero inteligente sobrecargado \* y los operadores \-\> no es mucho más lento que el acceso directo a los punteros sin formato.  
  
 Los punteros inteligentes tienen sus propias funciones miembro, a las que se accede mediante la notación “punto”.  Por ejemplo, algunos punteros inteligentes de STL tienen una función miembro de restablecimiento que libera la propiedad del puntero.  Esto es útil cuando se quiere liberar la memoria que es propiedad del puntero inteligente antes de que el puntero inteligente salga del ámbito, tal y como se muestra en el ejemplo siguiente.  
  
 [!code-cpp[smart_pointers_intro#3](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_3.cpp)]  
  
 Los punteros inteligentes suelen proporcionar un mecanismo para acceder directamente al puntero sin formato.  Los punteros inteligentes STL tienen una función miembro de `get` con este propósito y `CComPtr` tiene un miembro de clase `p` público.  Si proporciona acceso directo al puntero subyacente, puede utilizar el puntero inteligente para administrar la memoria en el propio código y continuar pasando el puntero sin formato en un código que no admita punteros inteligentes.  
  
 [!code-cpp[smart_pointers_intro#4](../cpp/codesnippet/CPP/smart-pointers-modern-cpp_4.cpp)]  
  
## Clases de punteros inteligentes  
 En la sección siguiente se resumen los distintos tipos de punteros inteligentes disponibles en el entorno de programación de Windows y se describe cuándo utilizarlos.  
  
 **Punteros inteligentes de la biblioteca estándar de C\+\+**  
 Utilice estos punteros inteligentes como primera opción para encapsular punteros a los objetos estándar de C\+\+ \(POCO\).  
  
-   `unique_ptr`    
    Permite exactamente un único propietario del puntero subyacente.  Utilice esta opción como predeterminada para los objetos POCO, a menos que sepa con certeza que necesita un objeto `shared_ptr`.  Puede moverse a un nuevo propietario, pero no se puede copiar ni compartir.  Sustituye a `auto_ptr`, que está desusado.  Comparado con `boost::scoped_ptr`,  `unique_ptr` es pequeño y eficaz; el tamaño es un puntero y admite referencias rvalue de inserción y extracción rápidas en colecciones STL.  Archivo de encabezado: `<memory>`.  Para obtener más información, vea [Cómo: Crear y usar instancias de unique\_ptr](../cpp/how-to-create-and-use-unique-ptr-instances.md) y [unique\_ptr \(Clase\)](../standard-library/unique-ptr-class.md).  
  
-   `shared_ptr`    
    Puntero inteligente con recuento de referencias.  Utilícelo cuando desee asignar un puntero sin formato a varios propietarios, por ejemplo, cuando devuelve una copia de un puntero desde un contenedor pero desea conservar el original.  El puntero sin formato no se elimina hasta que todos los propietarios de `shared_ptr` han salido del ámbito o, de lo contrario, han renunciado a la propiedad.  El tamaño es dos punteros: uno para el objeto y otro para el bloque de control compartido que contiene el recuento de referencias.  Archivo de encabezado: `<memory>`.  Para obtener más información, vea [Cómo: Crear y usar instancias de shared\_ptr](../cpp/how-to-create-and-use-shared-ptr-instances.md) y [shared\_ptr \(Clase\)](../standard-library/shared-ptr-class.md).  
  
-   `weak_ptr`    
    Puntero inteligente de caso especial para usarlo junto con `shared_ptr`.  `weak_ptr` proporciona acceso a un objeto que pertenece a una o varias instancias de `shared_ptr`, pero no participa en el recuento de referencias.  Utilícelo cuando desee observar un objeto, pero no quiere que permanezca activo.  Es necesario en algunos casos para interrumpir las referencias circulares entre instancias de `shared_ptr`.  Archivo de encabezado: `<memory>`.  Para obtener más información, vea [Cómo: Crear y usar instancias de weak\_ptr](../cpp/how-to-create-and-use-weak-ptr-instances.md) y [weak\_ptr \(Clase\)](../standard-library/weak-ptr-class.md).  
  
 **Punteros inteligentes para objetos COM \(programación clásica de Windows\)**  
 Cuando trabaje con objetos COM, encapsule los punteros de interfaz en un tipo de puntero inteligente adecuado.  Active Template Library \(ATL\) define varios punteros inteligentes para propósitos diferentes.  También puede usar el tipo de puntero inteligente `_com_ptr_t`, que el compilador utiliza cuando crea clases contenedoras de archivos .tlb.  Es la mejor opción si no desea incluir los archivos de encabezado ATL.  
  
 [CComPtr Class](../atl/reference/ccomptr-class.md)  
 Utilice esta opción a menos que no puede usar ATL.  Realiza el recuento de referencias mediante los métodos `AddRef` y de `Release`.  Para obtener más información, vea [Cómo: Crear y usar instancias de CComPtr y CComQIPtr](../cpp/how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).  
  
 [CComQIPtr Class](../atl/reference/ccomqiptr-class.md)  
 Se parece a `CComPtr`, pero también proporciona la sintaxis simplificada para llamar a `QueryInterface` en objetos COM.  Para obtener más información, vea [Cómo: Crear y usar instancias de CComPtr y CComQIPtr](../cpp/how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md).  
  
 [CComHeapPtr Class](../atl/reference/ccomheapptr-class.md)  
 Puntero inteligente a objetos que utilizan `CoTaskMemFree` para liberar memoria.  
  
 [CComGITPtr Class](../atl/reference/ccomgitptr-class.md)  
 Puntero inteligente para las interfaces que se obtienen de la tabla de interfaz global \(GIT\).  
  
 [\_com\_ptr\_t \(Clase\)](../cpp/com-ptr-t-class.md)  
 Se parece a `CComQIPtr` en funcionalidad, pero no depende de los encabezados ATL.  
  
 **Punteros inteligentes ATL para objetos POCO**  
 Además de punteros inteligentes para los objetos COM, ATL también define punteros inteligentes y colecciones de punteros inteligentes para objetos estándar de C\+\+.  En la programación clásica de Windows, estos tipos son alternativas útiles a las colecciones STL, especialmente cuando no es necesaria la portabilidad de código o cuando no se quiere mezclar los modelos de programación de STL y ATL.  
  
 [CAutoPtr Class](../atl/reference/cautoptr-class.md)  
 Puntero inteligente que exige una propiedad única al transferir la propiedad en la copia.  Puede compararse con la clase `std::auto_ptr` desusada.  
  
 [CHeapPtr Class](../atl/reference/cheapptr-class.md)  
 Puntero inteligente para objetos asignados mediante la función [malloc](../c-runtime-library/reference/malloc.md) de C.  
  
 [CAutoVectorPtr Class](../atl/reference/cautovectorptr-class.md)  
 Puntero inteligente para matrices que se asignan mediante `new[]`.  
  
 [CAutoPtrArray Class](../atl/reference/cautoptrarray-class.md)  
 Clase que encapsula una matriz de elementos `CAutoPtr`.  
  
 [CAutoPtrList Class](../atl/reference/cautoptrlist-class.md)  
 Clase que encapsula los métodos para manipular una lista de nodos de `CAutoPtr`.  
  
## Vea también  
 [Aquí está otra vez C\+\+](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referencia de lenguaje C\+\+](../cpp/cpp-language-reference.md)   
 [Biblioteca estándar de C\+\+](../standard-library/cpp-standard-library-reference.md)   
 [información general: administración de memoria en C\+\+](http://msdn.microsoft.com/es-es/2201885d-3d91-4a6e-aaa6-7a554e0362a8)