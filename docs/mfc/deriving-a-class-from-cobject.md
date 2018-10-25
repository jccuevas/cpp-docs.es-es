---
title: Derivar una clase de CObject | Microsoft Docs
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
ms.openlocfilehash: a102eae0dd5f96d74f7258c10c5bcce55c3a6443
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065375"
---
# <a name="deriving-a-class-from-cobject"></a>Derivar una clase de CObject

En este artículo se describe los pasos mínimos necesarios para derivar una clase de [CObject](../mfc/reference/cobject-class.md). Otros `CObject` clase artículos describen los pasos necesarios para aprovechar las ventajas específicas de `CObject` características, como la serialización y la compatibilidad de depuración de diagnóstico.

En las discusiones de `CObject`, los términos "archivo de interfaz" y "archivo de implementación" se usan con frecuencia. El archivo de interfaz (denominada a menudo el archivo de encabezado, o. H) contiene la declaración de clase y cualquier otra información necesaria para usar la clase. El archivo de implementación (o). Archivo CPP) contiene la definición de clase, así como el código que implementa las funciones miembro de clase. Por ejemplo, para una clase denominada `CPerson`, lo habitual sería crear un archivo de interfaz denominado PERSON. H y un archivo de implementación denominada PERSON. CPP. Sin embargo, para algunas clases pequeñas que no se compartirá entre aplicaciones, a veces es más fácil combinar la interfaz y la implementación en una sola. Archivo CPP.

Puede elegir entre cuatro niveles de funcionalidad al derivar una clase de `CObject`:

- Funcionalidad básica: No se admite para la serialización o la información de clases en tiempo de ejecución, pero incluye la administración de memoria para diagnósticos.

- Funcionalidad básica además de soporte técnico para obtener información de clase en tiempo de ejecución.

- Funcionalidad básica más compatibilidad con la información de clases en tiempo de ejecución y la creación dinámica.

- Funcionalidad básica más compatibilidad con información de clases en tiempo de ejecución, la creación dinámica y la serialización.

Clases diseñadas para su reutilización (los que se usará más adelante como clases base) deben incluir al menos soporte técnico de la clase de tiempo de ejecución y compatibilidad con la serialización, si se prevé la necesidad de serialización futuros.

Elija el nivel de funcionalidad mediante el uso de macros de declaración e implementación específicas en la declaración y la implementación de las clases que deriva de `CObject`.

En la tabla siguiente se muestra la relación entre las macros utilizadas para admitir la serialización y la información de tiempo de ejecución.

### <a name="macros-used-for-serialization-and-run-time-information"></a>Macros utilizadas para la serialización y la información de tiempo de ejecución

|Macro utilizada|CObject:: IsKindOf|CRuntimeClass::<br /><br /> CreateObject|CArchive::operator >><br /><br /> CArchive::operator <<|
|----------------|-----------------------|--------------------------------------|-------------------------------------------------------|
|Básico `CObject` funcionalidad|No|No|No|
|`DECLARE_DYNAMIC`|Sí|No|No|
|`DECLARE_DYNCREATE`|Sí|Sí|No|
|`DECLARE_SERIAL`|Sí|Sí|Sí|

#### <a name="to-use-basic-cobject-functionality"></a>Para usar la funcionalidad básica de CObject

1. Use la sintaxis de C++ normal para derivar la clase de `CObject` (o desde una clase derivada de `CObject`).

   El ejemplo siguiente muestra el caso más simple, la derivación de una clase desde `CObject`:

   [!code-cpp[NVC_MFCCObjectSample#1](../mfc/codesnippet/cpp/deriving-a-class-from-cobject_1.h)]

Normalmente, sin embargo, es posible que desee reemplazar algunas de `CObject`de las funciones miembro para controlar los detalles de la nueva clase. Por ejemplo, es posible que normalmente desea invalidar el `Dump` función de `CObject` para proporcionar la información de depuración para el contenido de la clase. Para obtener más información sobre cómo invalidar `Dump`, consulte el artículo [diagnósticos: volcar el contenido de objeto](/previous-versions/visualstudio/visual-studio-2010/sc15kz85). También puede invalidar el `AssertValid` función de `CObject` para proporcionar una prueba personalizada para validar la coherencia de los miembros de datos de objetos de clase. Para obtener una descripción de cómo invalidar `AssertValid`, consulte [MFC ASSERT_VALID y CObject:: AssertValid](/previous-versions/visualstudio/visual-studio-2010/38z04tfa).

El artículo [especificar niveles de funcionalidad](../mfc/specifying-levels-of-functionality.md) se describe cómo especificar otros niveles de funcionalidad, incluida la información de clase en tiempo de ejecución, creación dinámica de objetos y serialización.

## <a name="see-also"></a>Vea también

[Uso de CObject](../mfc/using-cobject.md)

