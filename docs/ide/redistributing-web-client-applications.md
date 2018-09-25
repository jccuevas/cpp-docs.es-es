---
title: Redistribuir aplicaciones cliente web | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Web applications [C++], redistributing
- deploying applications [C++], Web applications
- Internet applications [C++], redistributing
- application deployment [C++], Web applications
ms.assetid: fe05988b-dee8-4a46-b381-016b5103a6bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cdde0f8d4edc13e8c1e1a53d8f4393dc7c2dac40
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372475"
---
# <a name="redistributing-web-client-applications"></a>Redistribuir aplicaciones cliente web

Si en la aplicación se usan las clases de MFC que implementan el control WebBrowser (por ejemplo, `CHtmlView` o `CHtmlEditView`), en el equipo de destino debe estar instalado Microsoft Internet Explorer 4.0 o una versión posterior como mínimo.

Instalar la versión más reciente de Internet Explorer también garantiza que el equipo de destino tiene los archivos de control comunes más recientes.

En el artículo de Knowledge Base siguiente obtendrá información sobre cómo instalar los componentes mínimos de Internet Explorer:

- Q185375, HOWTO: Create a Single EXE Install of Internet Explorer ([http://support.microsoft.com/support/kb/articles/q185/3/75.asp](http://support.microsoft.com/support/kb/articles/q185/3/75.asp)) (CÓMO: Crear una instalación EXE única de Internet Explorer).

Puede encontrar los artículos de Knowledge Base en la biblioteca de MSDN o en [http://support.microsoft.com](http://support.microsoft.com).

## <a name="see-also"></a>Vea también

[Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)