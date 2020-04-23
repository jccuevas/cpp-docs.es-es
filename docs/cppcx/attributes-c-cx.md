---
title: Atributos (C++/CX)
ms.date: 12/30/2016
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
ms.openlocfilehash: b9e645de021e8618d1dc15a7d58dbbe5998e6fbc
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032387"
---
# <a name="attributes-ccx"></a>Atributos (C++/CX)

Un atributo es un tipo especial de clase ref que se puede anteponer entre corchetes a los tipos y métodos de Windows Runtime para especificar determinados comportamientos en la creación de metadatos. Varios atributos predefinidos (por ejemplo, [Windows::Foundation::Metadata::WebHostHidden)](/uwp/api/windows.foundation.metadata.webhosthiddenattribute)se utilizan normalmente en código C++/CX. En este ejemplo se muestra cómo se aplica el atributo a una clase:

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

## <a name="see-also"></a>Vea también

[Sistema de tipo (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Referencia del lenguaje C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)
