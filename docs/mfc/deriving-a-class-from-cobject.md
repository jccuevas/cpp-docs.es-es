---
title: Derivar una clase de CObject | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CObject
dev_langs:
- C++
helpviewer_keywords:
- DECLARE_DYNCREATE macro [MFC]
- DECLARE_SERIAL macro [MFC]
- macros [MFC], serialization
- serialization [MFC], macros
- DECLARE_DYNAMIC macro [MFC]
- derived classes [MFC], from CObject
- CObject class [MFC], deriving serializable classes
- CObject class [MFC], deriving from
ms.assetid: 5ea4ea41-08b5-4bd8-b247-c5de8c152a27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2d0b629617c1592387f3f959996fd3e9837242ea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349362"
---
# <a name="deriving-a-class-from-cobject"></a>Derivar una clase de CObject
Este artículo describen los pasos mínimos necesarios para derivar una clase de [CObject](../mfc/reference/cobject-class.md). Otros `CObject` artículos de la clase describen los pasos necesarios para aprovechar las ventajas específicas de `CObject` características, como la serialización y la compatibilidad de depuración de diagnóstico.  
  
 En las discusiones de `CObject`, los términos "archivo de interfaz" y "archivo de implementación" se usan con frecuencia. El archivo de interfaz (a menudo denominado archivo de encabezado, o. H) contiene la declaración de clase y cualquier otra información necesaria para utilizar la clase. El archivo de implementación (o). CPP) contiene la definición de clase, así como el código que implementa las funciones de miembro de clase. Por ejemplo, para una clase denominada `CPerson`, normalmente crearía un archivo de interfaz con el nombre de persona. H y un archivo de implementación denominado PERSON. CPP. Sin embargo, para algunas clases pequeñas que no se compartirá entre las aplicaciones, a veces es más fácil combinar la interfaz y la implementación en una sola. Archivo CPP.  
  
 Puede elegir entre cuatro niveles de funcionalidad cuando se deriva una clase de `CObject`:  
  
-   La funcionalidad básica: No se admite para la serialización o la información de clase en tiempo de ejecución pero incluye la administración de memoria para diagnósticos.  
  
-   Funcionalidad básica más compatibilidad con la información de clase en tiempo de ejecución.  
  
-   Funcionalidad básica más compatibilidad con la información de clase en tiempo de ejecución y la creación dinámica.  
  
-   Funcionalidad básica más compatibilidad para la serialización, la creación dinámica y la información de clase en tiempo de ejecución.  
  
 Clases diseñadas para su reutilización (aquellas que servirán después como clases base) como mínimo deben incluir compatibilidad con clases de tiempo de ejecución y compatibilidad con la serialización, si se prevé la necesidad de serialización futuras.  
  
 Elija el nivel de funcionalidad mediante el uso de macros de declaración e implementación específicas en la declaración y la implementación de las clases que deriva de `CObject`.  
  
 En la tabla siguiente se muestra la relación entre las macros utilizadas para admitir la serialización y la información de tiempo de ejecución.  
  
### <a name="macros-used-for-serialization-and-run-time-information"></a>Macros se utilizan para la serialización y la información de tiempo de ejecución  
  
|Macro utilizada|CObject:: IsKindOf|CRuntimeClass::<br /><br /> CreateObject|CArchive::operator >><br /><br /> CArchive::operator <<|  
|----------------|-----------------------|--------------------------------------|-------------------------------------------------------|  
|Básico `CObject` funcionalidad|No|No|No|  
|`DECLARE_DYNAMIC`|Sí|No|No|  
|`DECLARE_DYNCREATE`|Sí|Sí|No|  
|`DECLARE_SERIAL`|Sí|Sí|Sí|  
  
#### <a name="to-use-basic-cobject-functionality"></a>Para usar la funcionalidad básica de CObject  
  
1.  Use la sintaxis de C++ normal para derivar la clase de `CObject` (o desde una clase derivada de `CObject`).  
  
     En el ejemplo siguiente se muestra el caso más simple, la derivación de una clase desde `CObject`:  
  
     [!code-cpp[NVC_MFCCObjectSample#1](../mfc/codesnippet/cpp/deriving-a-class-from-cobject_1.h)]  
  
 Normalmente, sin embargo, puede invalidar algunas de las `CObject`de funciones de miembro para controlar los detalles de la nueva clase. Por ejemplo, normalmente puede invalidar la `Dump` función de `CObject` para proporcionar la información de depuración para el contenido de la clase. Para obtener más información sobre cómo invalidar `Dump`, vea el artículo [diagnósticos: volcar el contenido del objeto](http://msdn.microsoft.com/en-us/727855b1-5a83-44bd-9fe3-f1d535584b59). También puede invalidar el `AssertValid` función de `CObject` para proporcionar una prueba personalizada para validar la coherencia de los miembros de datos de objetos de clase. Para obtener una descripción de cómo invalidar `AssertValid`, consulte [MFC ASSERT_VALID y CObject:: AssertValid](http://msdn.microsoft.com/en-us/7654fb75-9e9a-499a-8165-0a96faf2d5e6).  
  
 El artículo [especificar niveles de funcionalidad](../mfc/specifying-levels-of-functionality.md) describe cómo especificar otros niveles de funcionalidad, incluida la información de clase en tiempo de ejecución, creación dinámica de objetos y serialización.  
  
## <a name="see-also"></a>Vea también  
 [Uso de CObject](../mfc/using-cobject.md)

