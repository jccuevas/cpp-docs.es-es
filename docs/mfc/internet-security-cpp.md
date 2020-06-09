---
title: Seguridad de Internet (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- code signing [MFC], Internet security
- sandboxing [MFC]
- digital signatures [MFC], Internet security
- code signing [MFC]
- Web application security [MFC]
- code access security [MFC], Internet security considerations
- security [MFC]
- security [MFC], Internet
- Internet applications [MFC], security
- Web application security [MFC], Internet security approaches
ms.assetid: bf0da697-81bc-41f0-83fa-d7f82ed83df8
ms.openlocfilehash: ce044014c5c2e13528cea8b982227b0ec8bc03fc
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621542"
---
# <a name="internet-security-c"></a>Seguridad de Internet (C++)

La seguridad del código es un problema importante para los desarrolladores y para los usuarios de aplicaciones de Internet. Hay riesgos: código malintencionado, código que se ha alterado y código de sitios o autores desconocidos.

Hay dos enfoques básicos para la seguridad al desarrollar para Internet. El primero se denomina "espacio aislado". En este enfoque, una aplicación está restringida a un conjunto determinado de API y se excluye de los potencialmente peligrosos, como la e/s de archivos, donde un programa podría destruir datos en el equipo de un usuario. La segunda se implementa mediante firmas digitales. Este enfoque se conoce como "shrinkwrap" para Internet. El código se comprueba y firma mediante la tecnología de clave privada y clave pública. Antes de ejecutar el código, se comprueba su firma digital para asegurarse de que el código proviene de un origen autenticado conocido y de que el código no se ha modificado desde que se firmó.

En el primer caso, confía en que la aplicación no hará ningún daño y confíe en el origen de la aplicación. En el segundo, se usan firmas digitales para comprobar la autenticidad. La firma digital es un estándar del sector que se usa para identificar y proporcionar detalles sobre el publicador del código. Su tecnología se basa en estándares, como RSA y X. 509. Los exploradores normalmente permiten a los usuarios elegir si desean descargar y ejecutar código de origen desconocido.

## <a name="see-also"></a>Consulte también

[Tareas de programación para Internet de MFC](mfc-internet-programming-tasks.md)<br/>
[Fundamentos de la programación para Internet de MFC](mfc-internet-programming-basics.md)
