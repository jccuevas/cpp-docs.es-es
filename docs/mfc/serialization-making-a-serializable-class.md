---
title: "Serialization: Making a Serializable (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases [C++], derivadas"
  - "CObject (clase), derivar clases serializables"
  - "constructores [C++], definir sin argumentos"
  - "DECLARE_SERIAL (macro)"
  - "constructor predeterminado"
  - "valores predeterminados [C++], constructor"
  - "IMPLEMENT_SERIAL (macro)"
  - "ningún constructor predeterminado"
  - "ningún constructor con argumentos"
  - "clase serializables"
  - "serialización [C++], clases serializables"
  - "Serialize (método), reemplazar"
  - "VERSIONABLE_SCHEMA (macro)"
ms.assetid: 59a14d32-1cc8-4275-9829-99639beee27c
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Serialization: Making a Serializable (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cinco pasos principales son necesarios para crear una clase serializable.  Se enumeran y se explican en las secciones siguientes:  
  
1.  [Derivar de la clase de CObject](#_core_deriving_your_class_from_cobject) \(o de alguna clase derivada de `CObject`\).  
  
2.  [Reemplazar la función miembro de Serialize](#_core_overriding_the_serialize_member_function).  
  
3.  [Mediante la macro de DECLARE\_SERIAL](#_core_using_the_declare_serial_macro) en la declaración de clase.  
  
4.  [Definir un constructor que no toma ningún argumento](#_core_defining_a_constructor_with_no_arguments).  
  
5.  [Mediante la macro de IMPLEMENT\_SERIAL en el archivo de implementación](#_core_using_the_implement_serial_macro_in_the_implementation_file) para la clase.  
  
 Si llama a `Serialize` directamente en lugar de a través de \>\> y \<\< operadores de [CArchive](../mfc/reference/carchive-class.md), los tres últimos pasos no son necesarios para la serialización.  
  
##  <a name="_core_deriving_your_class_from_cobject"></a> Derivar de la clase de CObject  
 El protocolo y la funcionalidad básicos de serialización se definen en la clase de `CObject` .  Si deriva la clase de `CObject` \(o una clase derivada de `CObject`\), como se muestra en la siguiente declaración de la clase `CPerson`, puede obtener acceso al protocolo de serialización y funcionalidad de `CObject`.  
  
##  <a name="_core_overriding_the_serialize_member_function"></a> Reemplazar la función miembro de Serialize  
 La función miembro de `Serialize` , que se define en la clase de `CObject` , es responsable realmente de serializar los datos necesarios capturar el estado actual de un objeto.  La función de `Serialize` tiene un argumento de `CArchive` que utilice para leer y escribir los datos de objeto.  El objeto de [CArchive](../mfc/reference/carchive-class.md) tiene una función miembro, `IsStoring`, que indica si `Serialize` está almacenando \(datos de escritura\) o carga \(datos de lectura\).  Mediante los resultados de `IsStoring` como guía, inserte los datos de objeto en el objeto de `CArchive` con el operador de inserción \(**\<\<**\) o datos de extraer con el operador de extracción \(**\>\>**\).  
  
 Considere una clase que se deriva de `CObject` y tiene dos nuevas variables miembro, tipos `CString` y **palabra**.  El siguiente fragmento de la declaración de clase muestra las nuevas variables miembro y la declaración de la función invalidada de miembro de `Serialize` :  
  
 [!code-cpp[NVC_MFCSerialization#1](../mfc/codesnippet/CPP/serialization-making-a-serializable-class_1.h)]  
  
#### Para reemplazar la función miembro de Serialize  
  
1.  Llame a la versión de la clase base de `Serialize` para asegurarse de que serializan a la parte heredado del objeto.  
  
2.  Inserte o extraer las variables miembro específicas a la clase.  
  
     Los operadores de inserción y de extracción interactúan con la clase del archivo para leer y escribir los datos.  El ejemplo siguiente se muestra cómo implementar `Serialize` para la clase de `CPerson` declarada anteriormente:  
  
     [!code-cpp[NVC_MFCSerialization#2](../mfc/codesnippet/CPP/serialization-making-a-serializable-class_2.cpp)]  
  
 También puede utilizar [CArchive::Read](../Topic/CArchive::Read.md) y el miembro de [CArchive::Write](../Topic/CArchive::Write.md) funciona para leer y escribir grandes cantidades de datos sin tipo.  
  
##  <a name="_core_using_the_declare_serial_macro"></a> Mediante la macro de DECLARE\_SERIAL  
 La macro de `DECLARE_SERIAL` se requiere en la declaración de clases que admitan la serialización, como se muestra aquí:  
  
 [!code-cpp[NVC_MFCSerialization#3](../mfc/codesnippet/CPP/serialization-making-a-serializable-class_3.h)]  
  
##  <a name="_core_defining_a_constructor_with_no_arguments"></a> Definir un Constructor sin argumentos  
 MFC requiere un constructor predeterminado cuando vuelve a crear los objetos según se deserializan \(carga desde el disco\).  El proceso de deserialización completará a todas las variables miembros con los valores necesarios para volver a crear el objeto.  
  
 Este constructor se puede declarar public, protected, o privado.  Si lo crea protegido o privado, ayuda a asegurarse de que se usará sólo las funciones de serialización.  El constructor debe colocar el objeto en un estado que permite que se elimine en caso necesario.  
  
> [!NOTE]
>  Si olvida definir un constructor sin argumentos en una clase que utilice macros de `DECLARE_SERIAL` y de `IMPLEMENT_SERIAL` , no obtendrá una “ninguna advertencia del compilador disponibles del constructor predeterminado” en la línea donde se utiliza la macro de `IMPLEMENT_SERIAL` .  
  
##  <a name="_core_using_the_implement_serial_macro_in_the_implementation_file"></a> Mediante la macro de IMPLEMENT\_SERIAL en el archivo de implementación  
 La macro de `IMPLEMENT_SERIAL` se utiliza para definir las diversas funciones necesarias al derivar una clase serializable de `CObject`.  Utiliza esta macro en el archivo de implementación \(.CPP\) para la clase.  Los primeros dos argumentos a la macro es el nombre de la clase y el nombre de la clase base inmediata.  
  
 El tercer argumento a esta macro es un número de esquema.  El número de esquema es esencialmente un número de versión para los objetos de la clase.  Utilice un mayor o igual que 0 entero para el número de esquema. \(No confunda este número de esquema con terminología de la base de datos\).  
  
 El código comprueba de serialización de MFC el número del esquema al leer objetos en memoria.  Si no coincide con el número del esquema del objeto en el disco el número del esquema de la clase en la memoria, la biblioteca producirá `CArchiveException`, impidiendo que el programa lee una versión incorrecta del objeto.  
  
 Si desea que la función miembro de `Serialize` pueda leer varias versiones \(es decir, archivos escritos en versiones diferentes de la aplicación\) puede utilizar el valor **VERSIONABLE\_SCHEMA** como argumento a la macro de `IMPLEMENT_SERIAL` .  Para obtener información de uso y un ejemplo, vea la función miembro de `GetObjectSchema` de la clase `CArchive`.  
  
 El ejemplo siguiente se muestra cómo utilizar `IMPLEMENT_SERIAL` para una clase, `CPerson`, que se deriva de `CObject`:  
  
 [!code-cpp[NVC_MFCSerialization#4](../mfc/codesnippet/CPP/serialization-making-a-serializable-class_4.cpp)]  
  
 Una vez que tiene una clase serializable, puede serializar objetos de clase, como se describe en el artículo [Serialización: Serialización de un objeto](../mfc/serialization-serializing-an-object.md).  
  
## Vea también  
 [Serialización](../mfc/serialization-in-mfc.md)