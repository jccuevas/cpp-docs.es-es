---
title: 'Serialization: Making a Serializable (Clase)'
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
ms.openlocfilehash: 9648bd4f516a5f174534336b1ca3b42bb51ca0c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372702"
---
# <a name="serialization-making-a-serializable-class"></a>Serialization: Making a Serializable (Clase)

Se requieren cinco pasos principales para que una clase sea serializable. Se enumeran a continuación y se explican en las siguientes secciones:

1. [Derivar la clase de CObject](#_core_deriving_your_class_from_cobject) (o de `CObject`alguna clase derivada de ).

1. [Reemplazar la función miembro Serialize](#_core_overriding_the_serialize_member_function).

1. [Mediante la macro DECLARE_SERIAL](#_core_using_the_declare_serial_macro) en la declaración de clase.

1. [Definir un constructor que no toma ningún argumento.](#_core_defining_a_constructor_with_no_arguments)

1. [El uso de la macro IMPLEMENT_SERIAL en el archivo](#_core_using_the_implement_serial_macro_in_the_implementation_file) de implementación de la clase.

Si llama `Serialize` directamente en lugar de a través de los operadores >> y << de [CArchive](../mfc/reference/carchive-class.md), los tres últimos pasos no son necesarios para la serialización.

## <a name="deriving-your-class-from-cobject"></a><a name="_core_deriving_your_class_from_cobject"></a>Derivación de su clase de CObject

El protocolo de serialización básico `CObject` y la funcionalidad se definen en la clase. Al derivar la `CObject` clase de (o de `CObject`una clase derivada de `CPerson`), como se muestra en la `CObject`siguiente declaración de clase , se obtiene acceso al protocolo de serialización y a la funcionalidad de .

## <a name="overriding-the-serialize-member-function"></a><a name="_core_overriding_the_serialize_member_function"></a>Reemplazar la función miembro Serialize

La `Serialize` función miembro, que `CObject` se define en la clase, es responsable de serializar realmente los datos necesarios para capturar el estado actual de un objeto. La `Serialize` función `CArchive` tiene un argumento que utiliza para leer y escribir los datos del objeto. El [CArchive](../mfc/reference/carchive-class.md) objeto tiene `IsStoring`una función `Serialize` miembro, , que indica si está almacenando (escribiendo datos) o cargando (leer datos). Utilizando los `IsStoring` resultados de como guía, puede insertar `CArchive` los datos del**<** objeto en el objeto con**>>** el operador de inserción ( ) o extraer datos con el operador de extracción ( ).

Considere una clase que `CObject` se deriva de y tiene `CString` dos nuevas variables miembro, de tipos y **WORD**. El siguiente fragmento de declaración de clase muestra las `Serialize` nuevas variables miembro y la declaración para la función miembro invalidada:

[!code-cpp[NVC_MFCSerialization#1](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_1.h)]

#### <a name="to-override-the-serialize-member-function"></a>Para invalidar el Serialize función miembro

1. Llame a la `Serialize` versión de la clase base para asegurarse de que se serializa la parte heredada del objeto.

1. Inserte o extraiga las variables miembro específicas de la clase.

   Los operadores de inserción y extracción interactúan con la clase de archivado para leer y escribir los datos. En el ejemplo siguiente `Serialize` se `CPerson` muestra cómo implementar para la clase declarada anteriormente:

   [!code-cpp[NVC_MFCSerialization#2](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_2.cpp)]

También puede utilizar las funciones miembro [CArchive::Read](../mfc/reference/carchive-class.md#read) y [CArchive::Write](../mfc/reference/carchive-class.md#write) para leer y escribir grandes cantidades de datos sin tipo.

## <a name="using-the-declare_serial-macro"></a><a name="_core_using_the_declare_serial_macro"></a>Uso de la macro DECLARE_SERIAL

La macro DECLARE_SERIAL es necesaria en la declaración de clases que admitirán la serialización, como se muestra aquí:

[!code-cpp[NVC_MFCSerialization#3](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_3.h)]

## <a name="defining-a-constructor-with-no-arguments"></a><a name="_core_defining_a_constructor_with_no_arguments"></a>Definición de un constructor sin argumentos

MFC requiere un constructor predeterminado cuando vuelve a crear los objetos a medida que se deserializan (cargados desde el disco). El proceso de deserialización rellenará todas las variables miembro con los valores necesarios para volver a crear el objeto.

Este constructor se puede declarar público, protegido o privado. Si lo hace protegido o privado, ayudará a asegurarse de que solo lo usarán las funciones de serialización. El constructor debe colocar el objeto en un estado que permita eliminarlo si es necesario.

> [!NOTE]
> Si olvida definir un constructor sin argumentos en una clase que usa las macros DECLARE_SERIAL y IMPLEMENT_SERIAL, obtendrá una advertencia del compilador "no hay constructor predeterminado disponible" en la línea donde se usa la macro IMPLEMENT_SERIAL.

## <a name="using-the-implement_serial-macro-in-the-implementation-file"></a><a name="_core_using_the_implement_serial_macro_in_the_implementation_file"></a>Uso de la macro IMPLEMENT_SERIAL en el archivo de implementación

La macro IMPLEMENT_SERIAL se utiliza para definir las distintas `CObject`funciones necesarias al derivar una clase serializable de . Utilice esta macro en el archivo de implementación (. CPP) para su clase. Los dos primeros argumentos de la macro son el nombre de la clase y el nombre de su clase base inmediata.

El tercer argumento de esta macro es un número de esquema. El número de esquema es esencialmente un número de versión para los objetos de la clase. Utilice un entero mayor o igual que 0 para el número de esquema. (No confunda este número de esquema con la terminología de la base de datos.)

El código de serialización MFC comprueba el número de esquema al leer objetos en la memoria. Si el número de esquema del objeto en el disco no coincide con `CArchiveException`el número de esquema de la clase en memoria, la biblioteca producirá un , impidiendo que el programa lea una versión incorrecta del objeto.

Si desea `Serialize` que la función miembro pueda leer varias versiones, es decir, archivos escritos con diferentes versiones de la aplicación, puede usar el valor *VERSIONABLE_SCHEMA* como argumento para la macro de IMPLEMENT_SERIAL. Para obtener información de uso `GetObjectSchema` y un `CArchive`ejemplo, vea la función miembro de la clase .

En el ejemplo siguiente se muestra `CPerson`cómo utilizar IMPLEMENT_SERIAL `CObject`para una clase, , que se deriva de:

[!code-cpp[NVC_MFCSerialization#4](../mfc/codesnippet/cpp/serialization-making-a-serializable-class_4.cpp)]

Una vez que tenga una clase serializable, puede serializar objetos de la clase, como se describe en el artículo [Serialización: serializar un objeto](../mfc/serialization-serializing-an-object.md).

## <a name="see-also"></a>Consulte también

[Serialización](../mfc/serialization-in-mfc.md)
