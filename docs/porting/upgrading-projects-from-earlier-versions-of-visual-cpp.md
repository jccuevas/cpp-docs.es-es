---
title: Actualizar C++ proyectos desde versiones anteriores de Visual Studio
description: Cómo actualizar proyectos de Microsoft C++ desde versiones anteriores de Visual Studio.
ms.date: 01/21/2020
helpviewer_keywords:
- 32-bit code porting
- upgrading Visual C++ applications, 32-bit code
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
ms.openlocfilehash: a18d2dbabdeec0f283fb4eca7ed52e616f9d224a
ms.sourcegitcommit: b67b08472b6f1ee8f1c5684bba7056d3e0fc745f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2020
ms.locfileid: "76725726"
---
# <a name="upgrade-c-projects-from-earlier-versions-of-visual-studio"></a>Actualizar C++ proyectos desde versiones anteriores de Visual Studio

Para actualizar un proyecto creado en una versión anterior de Visual Studio, solo tiene que abrir el proyecto en la versión más reciente de Visual Studio. Visual Studio ofrece la actualización del proyecto al esquema actual.

Si elige **no**, el proyecto no se actualizará. En el caso de los proyectos creados en Visual Studio 2010 y versiones posteriores, puede seguir usando el proyecto en la versión más reciente de Visual Studio. Solo tiene que establecer las propiedades del proyecto para seguir teniendo como destino el conjunto de herramientas anterior. Si deja la versión anterior de Visual Studio en el equipo, su conjunto de herramientas está disponible en versiones posteriores. Por ejemplo, si el proyecto debe seguir ejecutándose en Windows XP, puede actualizar a Visual Studio 2019. A continuación, especifique el conjunto de herramientas como v141_xp o anterior en las propiedades del proyecto. Para obtener más información, vea [Use native multi-targeting in Visual Studio to build old projects](use-native-multi-targeting.md) (Usar compatibilidad nativa con múltiples versiones en Visual Studio para compilar proyectos antiguos).

Si elige **sí**, el proyecto se actualizará en su lugar. No se puede volver a convertir a la versión anterior. En escenarios de actualización, esta es la razón por la que se recomienda realizar una copia de seguridad de los archivos de proyecto y de solución existentes.

## <a name="upgrade-reports"></a>Actualizar informes

Al actualizar un proyecto, obtendrá un informe de actualización. El informe también se guarda en la carpeta del proyecto como UpgradeLog. htm. El informe de actualización muestra un resumen de los problemas encontrados durante la conversión. Muestra información acerca de los cambios que se realizaron, entre los que se incluyen:

- Propiedades del proyecto.

- Archivos de inclusión.

- Código que ya no se compila correctamente debido a las mejoras de conformidad del compilador o a los cambios en el estándar.

- Código que se basa en las características de Windows o Visual Studio que ya no están disponibles. O, los archivos de encabezado que no se incluyen en una instalación predeterminada de Visual Studio o que se han quitado del producto.

- Código que ya no se compila debido a cambios en las API, como las API cuyo nombre ha cambiado, firmas de función cambiadas o funciones en desuso.

- Código que ya no se compila debido a cambios en los diagnósticos, como una advertencia que se convierte en un error.

- Errores del enlazador debido a las bibliotecas que se cambiaron, especialmente cuando se utiliza/NODEFAULTLIB.

- Errores en tiempo de ejecución o resultados inesperados debido a cambios de comportamiento.

- Errores que se introdujeron en las herramientas. Si encuentra un problema, informe al equipo visual C++ a través de los canales de soporte técnico normales o mediante la página de la comunidad de desarrolladores de [Visual Studio C++ ](https://developercommunity.visualstudio.com/spaces/62/index.html) .

Algunos proyectos y soluciones actualizados se pueden compilar correctamente sin modificarlos. Sin embargo, es probable que la mayoría de los proyectos requieran cambios en la configuración del proyecto y en el código fuente. No hay ninguna manera correcta de solucionar estos problemas, pero se recomienda usar un enfoque por fases. Antes de empezar, revise la [información general de los posibles problemas de actualización](../porting/overview-of-potential-upgrade-issues-visual-cpp.md) para obtener más información sobre muchos tipos de errores comunes.

1. Establezca el conjunto de herramientas C++ de la plataforma, el estándar del lenguaje y la versión Windows SDK (si procede) a las versiones preferidas. ( **Propiedades del** **proyecto** >  > **propiedades de configuración** > **General**)

1. Si tiene muchos errores, puede desactivar temporalmente algunas opciones mientras las corrige. Para desactivar la opción [/permissive-](../build/reference/permissive-standards-conformance.md) , use las **propiedades** de **Project** >  > **propiedades de configuración** > **lenguaje** **C/C++**  > . Para desactivar la opción [de análisis de código](/visualstudio/code-quality/code-analysis-for-c-cpp-overview) , use **propiedades** del **proyecto** >  > **propiedades de configuración** > análisis de **código**.

1. Asegúrese de que todas las dependencias están presentes y de que las rutas de acceso de inclusión o las ubicaciones de biblioteca son correctas. (Propiedades del**proyecto** ** >  > ** **propiedades de configuración** > directorios de **VC + +** )

1. Identifique y corrija los errores causados por las referencias a las API que ya no existen.

1. Corrija los errores restantes que impidan la compilación. Consulte [información general sobre posibles problemas de actualización](../porting/overview-of-potential-upgrade-issues-visual-cpp.md) para las correcciones de errores comunes.

1. Vuelva a activar **/permissive-** y corrija los errores nuevos causados por código no compatible que se compiló previamente en MSVC.

1. Active el análisis de código para identificar los posibles problemas o los patrones de codificación obsoletos que ya no se consideran aceptables. Si el análisis de código marca muchos errores, puede desactivar algunas de las advertencias para centrarse primero en las más importantes. El IDE puede ayudar con correcciones rápidas para algunos tipos de problemas.

1. Tenga en cuenta otras oportunidades para modernizar el código. Por ejemplo, reemplace los algoritmos y las estructuras de datos personalizados por C++ los de la biblioteca estándar, o por la biblioteca de código abierto de Boost. Mediante el uso de características estándar, es más fácil para otros usuarios mantener el código. Puede estar seguro de que este código está bien probado y revisado por muchos expertos en el Comité de estándares y la C++ comunidad más amplia.

En caso de errores difíciles de corregir, intente buscar o publicar una pregunta en Stack Overflow o [ C++ ](https://developercommunity.visualstudio.com/spaces/62/index.html)en la comunidad de desarrolladores.

## <a name="in-this-section"></a>En esta sección

[Información general sobre posibles problemas de actualización](overview-of-potential-upgrade-issues-visual-cpp.md)\
[Actualice el código al\ de CRT universal](upgrade-your-code-to-the-universal-crt.md)
[Actualizar winver y _WIN32_WINNT](modifying-winver-and-win32-winnt.md)\
[Corrección de las dependencias en los\ internos de la biblioteca](fix-your-dependencies-on-library-internals.md)
[Problemas de migración de punto flotante](floating-point-migration-issues.md)\
[características desusadas en Visual Studio 2019\ C++ ](features-deprecated-in-visual-studio.md)
\ de [VCBUILD frente a MSBuild](build-system-changes.md)
[Puerto de bibliotecas de terceros](porting-third-party-libraries.md)

## <a name="see-also"></a>Vea también

[Novedades de Visual C++ en Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)\
[Historial C++ de cambios visuales 2003-2015](../porting/visual-cpp-change-history-2003-2015.md)\
[Comportamiento no estándar](../cpp/nonstandard-behavior.md)\
[Aplicaciones de datos de Puerto](../data/data-access-programming-mfc-atl.md)
