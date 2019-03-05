---
title: 'Serialización: Crear una clase Serializable'
ms.date: 11/04/2016
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
ms.openlocfilehash: 995744381c8f82dc637e4aa0452e37af170b168b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281465"
---
# <a name="serialization-making-a-serializable-class"></a>Serialización: Crear una clase Serializable

Cinco pasos principales son necesarios para hacer que una clase sea serializable. Se enumeran a continuación y se explica en las secciones siguientes:

1. [Derivar la clase de CObject](#_core_deriving_your_class_from_cobject) (o de una clase derivada de `CObject`).

1. [Reemplazar la función miembro Serialize](#_core_overriding_the_serialize_member_function).

1. [Utilizar la macro DECLARE_SERIAL](#_core_using_the_declare_serial_macro) en la declaración de clase.

1. [Definir un constructor que no toma ningún argumento](#_core_defining_a_constructor_with_no_arguments).

1. [Utilizar la macro IMPLEMENT_SERIAL en el archivo de implementación](#_core_using_the_implement_serial_macro_in_the_implementation_file) para la clase.

Si se llama a `Serialize` directamente en lugar de a través del >> y << operadores de [CArchive](../mfc/reference/carchive-class.md), los tres últimos pasos no son necesarios para la serialización.

##  <a name="_core_deriving_your_class_from_cobject"></a> Derivar la clase de CObject

El protocolo de serialización básica y la funcionalidad que se definen en el `CObject` clase. Al derivar su clase de `CObject` (o desde una clase derivada de `CObject`), como se muestra en la siguiente declaración de clase `CPerson`, obtendrá acceso para el protocolo de serialización y la funcionalidad de `CObject`.

##  <a name="_core_overriding_the_serialize_member_function"></a> Reemplazar la función miembro Serialize

El `Serialize` función miembro, que se define en el `CObject` de clases, es responsable de serializar realmente los datos necesarios para capturar el estado actual de un objeto. El `Serialize` función tiene un `CArchive` argumento que utiliza para leer y escribir los datos del objeto. El [CArchive](../mfc/reference/carchive-class.md) objeto tiene una función miembro, `IsStoring`, lo que indica si `Serialize` es almacenamiento (escritura de datos) o cargando (lectura de datos). Uso de los resultados de `IsStoring` como guía, ya sea inserta los datos del objeto en el `CArchive` objeto con el operador de inserción (**<\<**) o extraer los datos con el operador de extracción ( **>>**).

Considere la posibilidad de una clase que se deriva de `CObject` y tiene dos nuevas variables miembro, tipos de `CString` y **WORD**. El siguiente fragmento de la declaración de clase muestra el nuevo miembro de las variables y la declaración de invalidado `Serialize` función miembro:

[!code-cpp[NVC_MFCSerialization#1](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_1.h)]

#### <a name="to-override-the-serialize-member-function"></a>Para invalidar la función miembro Serialize

1. Llame a la versión de la clase base `Serialize` para asegurarse de que la parte heredada del objeto se serializa.

1. Insertar o extraer las variables de miembro específicas de la clase.

   Los operadores de inserción y extracción interactúan con la clase de almacenamiento para leer y escribir los datos. El ejemplo siguiente muestra cómo implementar `Serialize` para el `CPerson` clase declarada anteriormente:

   [!code-cpp[NVC_MFCSerialization#2](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_2.cpp)]

También puede usar el [CArchive::Read](../mfc/reference/carchive-class.md#read) y [CArchive:: Write](../mfc/reference/carchive-class.md#write) funciones miembro para leer y escribir grandes cantidades de datos sin tipo.

##  <a name="_core_using_the_declare_serial_macro"></a> Utilizar la Macro DECLARE_SERIAL

La macro DECLARE_SERIAL se requiere en la declaración de clases que admite la serialización, como se muestra aquí:

[!code-cpp[NVC_MFCSerialization#3](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_3.h)]

##  <a name="_core_defining_a_constructor_with_no_arguments"></a> Definir un Constructor sin argumentos

MFC requiere un constructor predeterminado cuando se vuelve a crear los objetos se deserializan (cargado desde el disco). El proceso de deserialización rellene todas las variables miembro con los valores necesarios para volver a crear el objeto.

Este constructor puede declararse pública, protegida o privada. Si lo hace protegido o privado, ayudan a asegurarse de que solo se usan las funciones de serialización. El constructor debe colocar el objeto en un estado que permita que se puede eliminar si es necesario.

> [!NOTE]
>  Si se olvida de definir un constructor sin argumentos en una clase que utiliza las macros DECLARE_SERIAL y IMPLEMENT_SERIAL, obtendrá una advertencia del compilador "no hay disponible un constructor predeterminado" en la línea donde se usa la macro IMPLEMENT_SERIAL.

##  <a name="_core_using_the_implement_serial_macro_in_the_implementation_file"></a> Utilizar la Macro IMPLEMENT_SERIAL en el archivo de implementación

La macro IMPLEMENT_SERIAL se utiliza para definir las distintas funciones necesarios al derivar una clase serializable de `CObject`. Use esta macro en el archivo de implementación (. (CPP) de la clase. Los dos primeros argumentos a la macro son el nombre de la clase y el nombre de su clase base inmediata.

El tercer argumento para esta macro es un número de esquema. El número de esquema es esencialmente un número de versión para los objetos de la clase. Usar un número entero mayor o igual a 0 para el número de esquema. (No confunda este número de esquema con la terminología de base de datos).

El código de serialización de MFC comprueba el número de esquema al leer objetos en memoria. Si el número de esquema del objeto en el disco no coincide con el número de esquema de la clase en la memoria, la biblioteca, se producirá un `CArchiveException`, impide que el programa leer una versión incorrecta del objeto.

Si desea que su `Serialize` función miembro sea capaz de leer varias versiones, es decir, los archivos escritos con diferentes versiones de la aplicación, puede usar el valor *VERSIONABLE_SCHEMA* como argumento a la IMPLEMENT_SERIAL macro. Para obtener información de uso y un ejemplo, vea el `GetObjectSchema` función miembro de clase `CArchive`.

En el ejemplo siguiente se muestra cómo utilizar IMPLEMENT_SERIAL para una clase, `CPerson`, que se deriva de `CObject`:

[!code-cpp[NVC_MFCSerialization#4](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_4.cpp)]

Una vez que una clase serializable, se puede serializar objetos de la clase, como se describe en el artículo [serialización: Serializar un objeto](../mfc/serialization-serializing-an-object.md).

## <a name="see-also"></a>Vea también

[Serialización](../mfc/serialization-in-mfc.md)
