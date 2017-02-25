---
title: "TN002: Formato de datos de objetos persistentes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CArchive (clase), compatibilidad con datos persistentes"
  - "objetos persistentes de C++"
  - "datos de objetos persistentes"
  - "TN002"
  - "VERSIONABLE_SCHEMA (macro)"
ms.assetid: 553fe01d-c587-4c8d-a181-3244a15c2be9
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# TN002: Formato de datos de objetos persistentes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta nota describe las rutinas de MFC que admiten los objetos persistentes de C\+\+ y el formato de los datos de objeto cuando se almacena en un archivo.  Solo se aplica a las clases con macros de [DECLARE\_SERIAL](../Topic/DECLARE_SERIAL.md) y de [IMPLEMENT\_SERIAL](../Topic/IMPLEMENT_SERIAL.md) .  
  
## El problema  
 Implementación de MFC para datos persistentes de los almacenes de datos para muchos objetos en una sola parte contigua de un archivo.  El método de `Serialize` de objeto traduce los datos de objeto en un formato binario compacto.  
  
 La implementación garantiza que todos los datos se guarda en el mismo formato mediante [CArchive Class](../mfc/reference/carchive-class.md).  Usa un objeto de `CArchive` como traductor.  Este objeto conserva desde el momento en que se crea hasta que se llame a [CArchive::Close](../Topic/CArchive::Close.md).  Se puede llamar a este método explícitamente por el programador o implícitamente el destructor cuando el programa termina el ámbito que contiene `CArchive`.  
  
 Esta nota describe la implementación de los miembros [CArchive::ReadObject](../Topic/CArchive::ReadObject.md) y [CArchive::WriteObject](../Topic/CArchive::WriteObject.md)de `CArchive` .  Encontrará el código para estas funciones en Arcobj.cpp, y la implementación principal para `CArchive` en Arccore.cpp.  El código de usuario no llama a `ReadObject` y `WriteObject` directamente.  En su lugar, estos objetos son utilizados por los operadores tipo\- seguros clase\- específicos de inserción y de extracción que se generan automáticamente las macros de `DECLARE_SERIAL` y de `IMPLEMENT_SERIAL` .  El código siguiente muestra cómo `WriteObject` y `ReadObject` se denominan implícita:  
  
```  
class CMyObject : public CObject  
{  
    DECLARE_SERIAL(CMyObject)  
};  
  
IMPLEMENT_SERIAL(CMyObj, CObject, 1)  
  
// example usage (ar is a CArchive&)  
CMyObject* pObj;  
CArchive& ar;  
ar << pObj;        // calls ar.WriteObject(pObj)  
ar >> pObj;        // calls ar.ReadObject(RUNTIME_CLASS(CObj))  
```  
  
## Objetos de guardar en el almacén \(CArchive::WriteObject\)  
 Los datos del encabezado de las etiquetas de `CArchive::WriteObject` de método que se utiliza para volver a crear el objeto.  Estos datos se compone de dos partes: el tipo de objeto y el estado del objeto.  Este método también es responsable de mantener la identidad del objeto que se establecerá en tipo, solo para guardar una copia única, independientemente del número de punteros a ese objeto \(punteros circulares incluida.  
  
 Guardar \(el insertar\) y restaurar objetos \(extrayendo\) se basa en varias “constantes del manifiesto.” Éstos son los valores almacenados en binario y proporcionan información importante al archivo \(observe el prefijo “w” indica cantidades de 16 bits\):  
  
|Tag|Descripción|  
|---------|-----------------|  
|wNullTag|Utilizado para punteros de objeto NULL \(0\).|  
|wNewClassTag|Indica que la descripción de la clase que sigue es nuevo en este contexto de archivo \(\- 1\).|  
|wOldClassTag|Indica que la clase de objeto leídos se ha considerado en este contexto \(0x8000\).|  
  
 Al almacenar objetos, el archivo mantiene [CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) \( `m_pStoreMap`\) que es una asignación de un objeto almacenado un identificador persistente de 32 bits \(PID\).  Este número se asigna a cada objeto único y a cada nombre de clase único que está guardado en el contexto del archivo.  Estos PIDs son secuencialmente el iniciar distribuido en 1.  Estos PIDs no tienen ningún significado fuera del ámbito del archivo y, en particular, no hay que confundir con números de registro u otros elementos de identidad.  
  
 En la clase de `CArchive` , los PIDs son de 32 bits, pero se colocan en tipo como de 16 bits a menos que sean mayores que 0x7FFE.  Los PIDs grandes se escriben como 0x7FFF seguido por PID de 32 bits.  Esto mantiene la compatibilidad con los proyectos creados en versiones anteriores.  
  
 Cuando se realiza una solicitud para guardar un objeto en un archivo \(normalmente mediante el operador global de inserción\), una comprobación se crea para un puntero NULL [CObject](../mfc/reference/cobject-class.md) .  Si el puntero es NULL, `wNullTag` se inserta en la secuencia de archivo.  
  
 Si el puntero no es NULL y se puede serializar \(la clase es una clase de `DECLARE_SERIAL` \), el código comprueba `m_pStoreMap` para ver si el objeto se ha guardado.  Si tiene, el código inserta PID de 32 bits asociado a dicho objeto en la secuencia de archivo.  
  
 Si el objeto no se ha guardado anteriormente, hay dos posibilidades a considerar: o el objeto y el tipo exacto \(es decir, clase\) del objeto son nuevos en este contexto de archivo, o el objeto es de un tipo exacto que ya.  Para determinar si se han considerado el tipo, el código que `m_pStoreMap` para un objeto de [Recursos](../mfc/reference/cruntimeclass-structure.md) que coincide con el objeto de `CRuntimeClass` asociado al objeto que fue guardado.  Si hay una coincidencia, `WriteObject` inserta una etiqueta que se `OR` bit\- mejor de `wOldClassTag` y de este índice.  Si `CRuntimeClass` es nuevo en este contexto de archivo, `WriteObject` asigna nuevo PID a esa clase y se inserta en el archivo, precedida por el valor de `wNewClassTag` .  
  
 Descriptor de esta clase se inserta en el archivo utilizando el método de `CRuntimeClass::Store` .  `CRuntimeClass::Store` inserta el número del esquema de la clase \(vea a continuación\) y el nombre del texto ASCII de la clase.  Observe que el uso del nombre de texto ASCII no garantiza la unicidad de archivo a través de aplicaciones.  Por consiguiente, debe etiqueta los archivos de datos evitar daños.  Después de la inserción de información de clase, el archivo coloca el objeto en `m_pStoreMap` y después llamar al método de `Serialize` para insertar datos clase\- concretos.  Colocar el objeto en `m_pStoreMap` antes de llamar a `Serialize` evita que varias copias del objeto se guardaron en el almacén.  
  
 Al volver al llamador inicial \(normalmente la raíz de la red de objetos\), debe llamar a [CArchive::Close](../Topic/CArchive::Close.md).  Si piensa realizar otras operaciones de [Archivo C](../mfc/reference/cfile-class.md), debe llamar al método [Vaciado](../Topic/CArchive::Flush.md) de `CArchive` para evitar daños del archivo.  
  
> [!NOTE]
>  Esta implementación impone un límite difícil de los índices 0x3FFFFFFE por contexto del archivo.  Este número representa el número máximo de objetos y clases únicos que se pueden guardar en un solo archivo, pero un único archivo de disco puede tener un número ilimitado de contextos de archivo.  
  
## Objetos de carga de almacén \(CArchive::ReadObject\)  
 Cargar objetos \(extrayendo\) utiliza el método de `CArchive::ReadObject` y es el inverso de `WriteObject`.  Como con `WriteObject`, `ReadObject` no llama directamente desde el código de usuario; el código de usuario debe llamar al operador tipo\- seguro de extracción que llama a `ReadObject` con `CRuntimeClass`esperado.  Esto garantiza la integridad del tipo de la operación de extracción.  
  
 Puesto que la implementación de `WriteObject` asignado aumentar los PIDs, comenzando por 1 \(predefinida 0 como objeto NULL\), la implementación de `ReadObject` puede utilizar una matriz para mantener el estado del contexto del archivo.  Cuando este número se lee del almacén, si PID es mayor que el límite superior actual de `m_pLoadArray`, `ReadObject` sabe que un nuevo objeto \(o la clase\) siguiente.  
  
## Números de esquema  
 El número de esquemas, que se asigna a la clase cuando el método de `IMPLEMENT_SERIAL` de clase se encuentra, es la “versión” de la implementación de la clase.  El esquema hace referencia a la implementación de la clase, no el número de veces que un objeto determinado se ha creado persistente \(denominado normalmente la versión del objeto\).  
  
 Si desea mantener varias implementaciones diferentes de la misma clase con el tiempo, aumentar el esquema cuando revise la implementación del método de `Serialize` de objeto le permite escribir código que puede cargar los objetos almacenados mediante las versiones de la implementación.  
  
 El método de `CArchive::ReadObject` producirá [CArchiveException](../mfc/reference/carchiveexception-class.md) cuando encuentra un número de esquema en el almacén persistente que difiere del número de esquema de la clase en memoria.  No es fácil recuperar de esta excepción.  
  
 Puede utilizar `VERSIONABLE_SCHEMA` combinado con \( `OR`bit a bit\) la versión del esquema para conservar esta excepción de iniciar.  Mediante `VERSIONABLE_SCHEMA`, el código puede tomar las medidas adecuadas en la función de `Serialize` comprobando el valor devuelto de [CArchive::GetObjectSchema](../Topic/CArchive::GetObjectSchema.md).  
  
## Al llamar a serializa directamente  
 En muchos casos la sobrecarga de esquema general del objeto de `WriteObject` y de `ReadObject` no es necesaria.  Éste es el caso habitual de serializar los datos en [CDocument](../mfc/reference/cdocument-class.md).  En este caso, el método de `Serialize` de `CDocument` se llama directamente, no con los operadores de extracción o inserción.  El contenido del documento pueden a su vez utilizar el esquema más general del objeto.  
  
 La llamada `Serialize` tiene directamente las ventajas y las desventajas siguientes:  
  
-   No se agrega ningún bytes adicionales al archivo antes o después de que se serializa el objeto.  Esto ocasiona los datos guardados menores, pero permite implementar las rutinas de `Serialize` que pueden controlar cualquier formato de archivo.  
  
-   Adapta MFC de modo que las implementaciones de `WriteObject` y de `ReadObject` y colecciones relacionadas no se vincularán en la aplicación a menos que necesite el esquema más general del archivo objeto para algún otro propósito.  
  
-   El código no tiene que recuperar de los antiguos números de esquema.  Esto hace que el código de serialización de documentos responsable de codificar los números de esquema, números de versión del formato de archivo, o los números de identificación utiliza el inicio de los archivos de datos.  
  
-   Cualquier objeto de que se serialice mediante una llamada directa a `Serialize` no debe utilizar `CArchive::GetObjectSchema` ni debe controlar el valor devuelto \(UINT\) \- 1 que indica que la versión era desconocido.  
  
 Dado que `Serialize` se llama directamente al documento, normalmente no es posible que los sub\- objetos document a las referencias de archivo al documento primario.  Estos objetos deben tener un puntero al documento contenedor explícitamente o utilizar la función de [CArchive::MapObject](../Topic/CArchive::MapObject.md) para asignar el puntero de `CDocument` a PID antes de que se almacenan estos punteros posteriores.  
  
 Como anteriormente, debe codificar la información de versión y de la clase personalmente cuando se llama a `Serialize` directamente, lo que permite cambiar el formato más adelante mientras mantiene la compatibilidad con más archivos anteriores.  La función de `CArchive::SerializeClass` puede llamar explícitamente antes directamente de serializar un objeto o antes de llamar a una clase base.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)