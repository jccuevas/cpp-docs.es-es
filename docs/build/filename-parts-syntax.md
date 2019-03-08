---
title: Sintaxis de las partes de un nombre de archivo
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, filename-parts
- filename-parts syntax in NMAKE
- NMAKE program, syntax
ms.assetid: 48fe38e0-3f3b-40e6-894c-330ee775a656
ms.openlocfilehash: 159558081fd9884f969ddc66833d927b8569a79b
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417481"
---
# <a name="filename-parts-syntax"></a>Sintaxis de las partes de un nombre de archivo

Sintaxis de partes del nombre de archivo de comandos representa componentes del primer nombre de archivo dependiente (que puede ser un dependiente implícito). Componentes de nombre de archivo son unidad, ruta de acceso, nombre base y extensión tal como se especifica, el archivo no tal como existe en el disco. Use **%s** para representar el nombre de archivo completo. Use **%&#124;**[*partes*]**F** (una barra vertical el signo de porcentaje) para representar las partes del nombre de archivo, donde *partes*puede ser cero o más de las siguientes letras en cualquier orden.

|Carta|Descripción|
|------------|-----------------|
|No hay ninguna letra|Nombre completo (igual que **%s**)|
|**d**|Unidad|
|**p**|Ruta de acceso|
|**f**|Nombre base del archivo|
|**e**|Extensión de archivo|

Por ejemplo, si el nombre de archivo es c:\prog.exe:

- %s será c:\prog.exe

- %&#124;F será c:\prog.exe

- %&#124;dF será c

- %&#124;pF será c:\

- %&#124;fF será prog

- %&#124;eF será exe

## <a name="see-also"></a>Vea también

[Comandos en un archivo MAKE](../build/commands-in-a-makefile.md)
