---
title: "Serialización: Crear una clase Serializable | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- serializable class [MFC]
- DECLARE_SERIAL macro [MFC]
- default constructor [MFC]
- VERSIONABLE_SCHEMA macro [MFC]
- classes [MFC], derived
- IMPLEMENT_SERIAL macro [MFC]
- no-arguments constructor [MFC]
- Serialize method, overriding
- defaults [MFC], constructor
- CObject class [MFC], deriving serializable classes
- constructors [MFC], defining with no arguments
- serialization [MFC], serializable classes
- no default constructor
ms.assetid: 59a14d32-1cc8-4275-9829-99639beee27c
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 22bb8144f3c83ca98bffa2f95e73eff31ddb89be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="serialization-making-a-serializable-class"></a>Serialization: Making a Serializable (Clase)
Cinco pasos principales necesarios para hacer que una clase serializable. Se enumeran a continuación y explica en las secciones siguientes:  
  
1.  [Derivar la clase de CObject](#_core_deriving_your_class_from_cobject) (o desde una clase derivada de `CObject`).  
  
2.  [Reemplazar la función miembro Serialize](#_core_overriding_the_serialize_member_function).  
  
3.  [Utilizar la macro DECLARE_SERIAL](#_core_using_the_declare_serial_macro) en la declaración de clase.  
  
4.  [Definir un constructor que no toma ningún argumento](#_core_defining_a_constructor_with_no_arguments).  
  
5.  [Utilizar la macro IMPLEMENT_SERIAL en el archivo de implementación](#_core_using_the_implement_serial_macro_in_the_implementation_file) para la clase.  
  
 Si se llama a `Serialize` directamente en lugar de a través del >> y << operadores de [CArchive](../mfc/reference/carchive-class.md), los tres últimos pasos no son necesarios para la serialización.  
  
##  <a name="_core_deriving_your_class_from_cobject"></a>Derivar la clase de CObject  
 El protocolo de serialización básica y la funcionalidad se definen en la `CObject` clase. Derive la clase de `CObject` (o desde una clase derivada de `CObject`), tal y como se muestra en la siguiente declaración de clase `CPerson`, se obtiene acceso para el protocolo de serialización y la funcionalidad de `CObject`.  
  
##  <a name="_core_overriding_the_serialize_member_function"></a>Reemplazar la función miembro Serialize  
 El `Serialize` función de miembro, que se define en el `CObject` de clases, es responsable de serializar realmente los datos necesarios para capturar el estado actual de un objeto. El `Serialize` función tiene un `CArchive` argumento que utiliza para leer y escribir los datos del objeto. El [CArchive](../mfc/reference/carchive-class.md) objeto tiene una función miembro, `IsStoring`, lo que indica si `Serialize` es almacenar (escritura de datos) o cargando (lectura de datos). Con los resultados de `IsStoring` como guía, ya sea insertar datos del objeto en el `CArchive` objeto con el operador de inserción (**<\<**) o extraer los datos con el operador de extracción ( **>>**).  
  
 Considere la posibilidad de una clase que se deriva de `CObject` y tiene dos nuevas variables miembro, tipos de `CString` y **WORD**. El siguiente fragmento de la declaración de clase muestra el nuevo miembro variables y la declaración para el invalidado `Serialize` función miembro:  
  
 [!code-cpp[NVC_MFCSerialization#1](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_1.h)]  
  
#### <a name="to-override-the-serialize-member-function"></a>Para invalidar la función miembro Serialize  
  
1.  Llame a la versión de la clase base de `Serialize` para asegurarse de que la parte heredada del objeto se serializa.  
  
2.  Insertar o extraer las variables de miembro específicas de la clase.  
  
     Los operadores de inserción y extracción interactúan con la clase de almacenamiento para leer y escribir los datos. En el ejemplo siguiente se muestra cómo implementar `Serialize` para el `CPerson` clase declarada anteriormente:  
  
     [!code-cpp[NVC_MFCSerialization#2](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_2.cpp)]  
  
 También puede usar el [CArchive::Read](../mfc/reference/carchive-class.md#read) y [CArchive:: Write](../mfc/reference/carchive-class.md#write) funciones de miembro para leer y escribir grandes cantidades de datos sin tipo.  
  
##  <a name="_core_using_the_declare_serial_macro"></a>Utilizar la Macro DECLARE_SERIAL  
 El `DECLARE_SERIAL` macro es necesario en la declaración de clases que admiten la serialización, como se muestra aquí:  
  
 [!code-cpp[NVC_MFCSerialization#3](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_3.h)]  
  
##  <a name="_core_defining_a_constructor_with_no_arguments"></a>Definir un Constructor sin argumentos  
 MFC requiere un constructor predeterminado cuando vuelve a crear los objetos se deserializan (cargado desde el disco). El proceso de deserialización se rellenará todas las variables miembro con los valores necesarios para volver a crear el objeto.  
  
 Este constructor puede declararse pública, protegida o privada. Si lo hace protegido o privado, para ayudar a asegurarse de que solo se usan las funciones de serialización. El constructor debe incluir el objeto en un estado que permita que se pueda eliminar si es necesario.  
  
> [!NOTE]
>  Si se olvida de definir un constructor sin argumentos en una clase que utiliza el `DECLARE_SERIAL` y `IMPLEMENT_SERIAL` macros, obtendrá una advertencia del compilador "no hay disponible un constructor predeterminado" en la línea donde el `IMPLEMENT_SERIAL` macro se usa.  
  
##  <a name="_core_using_the_implement_serial_macro_in_the_implementation_file"></a>Utilizar la Macro IMPLEMENT_SERIAL en el archivo de implementación  
 El `IMPLEMENT_SERIAL` macro se usa para definir las distintas funciones necesarios al derivar una clase serializable de `CObject`. Use esta macro en el archivo de implementación (. CPP) para la clase. Los dos primeros argumentos a la macro son el nombre de la clase y el nombre de su clase base inmediata.  
  
 El tercer argumento para esta macro es un número de esquema. El número de esquema es básicamente un número de versión para los objetos de la clase. Usar un número entero mayor o igual que 0 para el número de esquema. (No confunda este número de esquema con la terminología de base de datos).  
  
 El código de serialización de MFC comprueba el número de esquema al leer objetos en la memoria. Si el número de esquema del objeto en el disco no coincide con el número de esquema de la clase en la memoria, la biblioteca, se producirá un `CArchiveException`, impide que el programa leer una versión incorrecta del objeto.  
  
 Si desea que su `Serialize` función miembro que pueda leer varias versiones, es decir, los archivos escritos con versiones diferentes de la aplicación: puede usar el valor **VERSIONABLE_SCHEMA** como argumento para el `IMPLEMENT_SERIAL` macro. Para obtener información de uso y un ejemplo, vea el `GetObjectSchema` función miembro de clase `CArchive`.  
  
 En el ejemplo siguiente se muestra cómo usar `IMPLEMENT_SERIAL` para una clase, `CPerson`, que se deriva de `CObject`:  
  
 [!code-cpp[NVC_MFCSerialization#4](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_4.cpp)]  
  
 Una vez que tenga una clase serializable, es posible serializar objetos de la clase, como se describe en el artículo [serialización: serializar un objeto](../mfc/serialization-serializing-an-object.md).  
  
## <a name="see-also"></a>Vea también  
 [Serialización](../mfc/serialization-in-mfc.md)

