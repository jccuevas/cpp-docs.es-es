---
title: Derivar una clase de CObject
ms.date: 11/04/2016
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
ms.openlocfilehash: 860af88512acb33ff3035b3a04609165953d80a8
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446968"
---
# <a name="deriving-a-class-from-cobject"></a>Derivar una clase de CObject

En este artículo se describen los pasos mínimos necesarios para derivar una clase de [CObject](../mfc/reference/cobject-class.md). En otros artículos de la clase `CObject` se describen los pasos necesarios para aprovechar las características de `CObject` específicas, como la serialización y la compatibilidad con la depuración de diagnóstico.

En las discusiones de `CObject`, los términos "archivo de interfaz" y "archivo de implementación" se usan con frecuencia. El archivo de interfaz (a menudo denominado archivo de encabezado o. H File) contiene la declaración de clase y cualquier otra información necesaria para utilizar la clase. El archivo de implementación (o. Archivo CPP) contiene la definición de clase, así como el código que implementa las funciones miembro de clase. Por ejemplo, para una clase denominada `CPerson`, normalmente crearía un archivo de interfaz denominado PERSON. H y un archivo de implementación denominado PERSON. CPP. Sin embargo, para algunas clases pequeñas que no se compartirán entre las aplicaciones, a veces es más fácil combinar la interfaz y la implementación en un único. Archivo CPP.

Puede elegir entre cuatro niveles de funcionalidad al derivar una clase de `CObject`:

- Funcionalidad básica: no se admite la serialización o la información de clase en tiempo de ejecución, sino que incluye administración de la memoria de diagnóstico.

- Funcionalidad básica más compatibilidad con la información de clase en tiempo de ejecución.

- Funcionalidad básica más compatibilidad con la información de clase en tiempo de ejecución y la creación dinámica.

- Funcionalidad básica más compatibilidad con la información de clase en tiempo de ejecución, la creación dinámica y la serialización.

Las clases diseñadas para su reutilización (aquellas que más adelante actuarán como clases base) deben incluir, como mínimo, compatibilidad de clase en tiempo de ejecución y compatibilidad con la serialización, si se prevé cualquier necesidad de serialización futura.

Elija el nivel de funcionalidad mediante el uso de macros de declaración e implementación específicas en la declaración y la implementación de las clases que deriva de `CObject`.

En la tabla siguiente se muestra la relación entre las macros utilizadas para admitir la serialización e información en tiempo de ejecución.

### <a name="macros-used-for-serialization-and-run-time-information"></a>Macros utilizadas para la serialización e información en tiempo de ejecución

|Macro usada|CObject::IsKindOf|CRuntimeClass::<br /><br /> CreateObject|CArchive::operator>><br /><br /> CArchive:: Operator < <|
|----------------|-----------------------|--------------------------------------|-------------------------------------------------------|
|Funcionalidad básica de `CObject`|No|No|No|
|`DECLARE_DYNAMIC`|Sí|No|No|
|`DECLARE_DYNCREATE`|Sí|Sí|No|
|`DECLARE_SERIAL`|Sí|Sí|Sí|

#### <a name="to-use-basic-cobject-functionality"></a>Para usar la funcionalidad básica de CObject

1. Use la sintaxis C++ normal para derivar la clase de `CObject` (o de una clase derivada de `CObject`).

   En el ejemplo siguiente se muestra el caso más simple, la derivación de una clase de `CObject`:

   [!code-cpp[NVC_MFCCObjectSample#1](../mfc/codesnippet/cpp/deriving-a-class-from-cobject_1.h)]

Sin embargo, por lo general, puede que desee invalidar algunas de las funciones miembro de `CObject`para controlar los detalles de la nueva clase. Por ejemplo, puede que desee invalidar la función `Dump` de `CObject` para proporcionar la salida de depuración para el contenido de la clase. Para obtener más información sobre cómo invalidar `Dump`, consulte el artículo sobre la [Personalización del volcado de objetos](/previous-versions/visualstudio/visual-studio-2010/sc15kz85(v=vs.100)). También puede que desee invalidar la función `AssertValid` de `CObject` para proporcionar pruebas personalizadas para validar la coherencia de los miembros de datos de los objetos de clase. Para obtener una descripción de cómo invalidar `AssertValid`, vea [MFC ASSERT_VALID y CObject:: AssertValid](reference/diagnostic-services.md#assert_valid).

En el artículo [especificar niveles de funcionalidad](../mfc/specifying-levels-of-functionality.md) se describe cómo especificar otros niveles de funcionalidad, incluida la información de clases en tiempo de ejecución, la creación dinámica de objetos y la serialización.

## <a name="see-also"></a>Consulte también

[Uso de CObject](../mfc/using-cobject.md)
