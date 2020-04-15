---
title: Atributos (C++/CX)
ms.date: 12/30/2016
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
ms.openlocfilehash: 437432ce32497311a9a91237118d6088881662a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371881"
---
# <a name="attributes-ccx"></a>Atributos (C++/CX)

Un atributo es un tipo especial de clase ref que se puede anteponer entre corchetes a los tipos y métodos de Windows Runtime para especificar determinados comportamientos en la creación de metadatos. Varios atributos predefinidos (por ejemplo, [Windows::Foundation::Metadata::WebHostHidden)](/uwp/api/Windows.Foundation.Metadata.WebHostHiddenAttribute)se utilizan normalmente en código C++/CX. En este ejemplo se muestra cómo se aplica el atributo a una clase:

[!code-cpp[cx_attributes#01](../cppcx/codesnippet/CPP/cx_attributes/class1.h#01)]

## <a name="custom-attributes"></a>Personalización de atributos

También puedes definir atributos personalizados. Los atributos personalizados deben cumplir estas reglas de Windows En tiempo de ejecución:

- Los atributos personalizados solo pueden contener campos públicos.

- Los campos de atributos personalizados se pueden inicializar cuando el atributo se aplica a una clase.

- Un campo puede ser de uno de estos tipos:

  - int32 (int)

  - uint32 (int sin signo)

  - bool

  - Platform::String^

  - Windows::Foundation::HResult

  - Platform::Type^

  - clase de enumeración pública (incluye enumeraciones definidas por el usuario)

En el ejemplo siguiente se muestra cómo definir un atributo personalizado y e inicializarlo después cuando lo utilices.

[!code-cpp[cx_attributes#02](../cppcx/codesnippet/CPP/cx_attributes/class1.h#02)]

## <a name="see-also"></a>Consulte también

[Sistema de tipo (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Referencia del lenguaje C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)
