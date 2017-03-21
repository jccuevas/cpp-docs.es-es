---
layout: LandingPage
title: Acceso a datos en Visual C++
translationtype: Human Translation
ms.sourcegitcommit: f9e63f47a8df69b52a6a12688e84602981d20dae
ms.openlocfilehash: 807cf772d632f66f74a210985ff611fc31ee594a
ms.lasthandoff: 03/21/2017

---
# <a name="data-access-in-visual-c"></a>Acceso a datos en Visual C++

Prácticamente todos los productos de base de datos, SQL y NoSQL, proporcionan una interfaz para aplicaciones nativas de C++. La interfaz estándar de la industria es ODBC, que se admite en los principales productos de base de datos SQL y en muchos productos NoSQL. Para productos que no son de Microsoft, consulte al proveedor para obtener más información. También existen bibliotecas de terceros con diferentes términos de licencia.

Desde 2011, Microsoft cuenta con ODBC como el estándar de conexión para las aplicaciones nativas a bases de datos de Microsoft SQL Server, tanto locales como en la nube. Para más información, vea [Programación del acceso a datos \(MFC/ATL\)](data-access-programming-mfc-atl.md). Las bibliotecas de C++/CLI pueden usar los controladores nativos de ODBC o ADO.NET. Para más información, vea [Acceso a datos en ADO.NET(C++/CLI)](/dotnet/data-access-using-adonet-cpp-cli.md) y [Obtener acceso a los datos en Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/accessing-data-in-visual-studio).

<ul class="panelContent cardsF">
<li>
        <a href="/azure/sql-database/sql-database-develop-cplusplus-simple">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/azure/media/index/SQLDatabase.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Conexión a SQL Database mediante C y C++</h3>
                        <p>Conexión a Azure SQL Database desde aplicaciones de C o C++</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="https://github.com/Azure/azure-storage-cpp">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/azure/media/index/Storage.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Biblioteca de cliente de Microsoft Azure Storage para C++</h3>
                        <p>[Azure Storage](/azure/storage/storage-introduction) es una solución de almacenamiento en la nube para aquellas aplicaciones modernas que necesitan durabilidad, disponibilidad y escalabilidad para satisfacer las necesidades de sus clientes. Conectarse a Azure Storage desde C++ mediante la biblioteca de cliente de Azure Storage para C++.</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="https://blogs.msdn.microsoft.com/sqlnativeclient/2016/08/01/announcing-the-odbc-driver-13-1-for-sql-server/">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/media/common/i_drivers.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Controlador ODBC 13.1 para SQL Server: versión de Windows</h3>
                        <p>El controlador ODBC más reciente proporciona un acceso a datos sólido a aplicaciones basadas en Microsoft Azure SQL Database para C/C++ de Microsoft SQL Server 2016. Proporciona compatibilidad con las características incluidas Always Encrypted, Azure Active Directory y Grupos de disponibilidad AlwaysOn. También está disponible para MacOS y Linux.</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="https://msdn.microsoft.com/library/ms130892.aspx">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/media/common/i_api.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>SQL Server Native Client</h3>
                        <p>SQL Server Native Client es una interfaz de programación de aplicaciones (API) independiente de acceso a datos que se usa para OLE DB y ODBC, y que es compatible con SQL Server 2005-2014. Las aplicaciones nuevas deben usar el controlador ODBC 13.1 para SQL Server.</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/cpp/data/data-access-programming-mfc-atl">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/media/common/i_api.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Programación con Data Access</h3>
                        <p>Describe la programación de acceso a datos heredados con Visual C++, donde se suele utilizar una de las bibliotecas de clases, como Active Template Library (ATL) o Microsoft Foundation Class (MFC), que simplifican el trabajo con las API de bases de datos.</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/cpp/data/odbc/open-database-connectivity-odbc">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/media/common/i_multi-connect.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Conectividad abierta de bases de datos (ODBC)</h3>
                        <p>La biblioteca Microsoft Foundation Classes (MFC) proporciona clases para la programación con ODBC (Open Database Connectivity, Conectividad abierta de bases de datos).</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/cpp/data/oledb/ole-db-programming">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="/media/common/i_generic-database.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Programación de OLE DB</h3>
                        <p>Proporciona vínculos a temas conceptuales que describen la tecnología de base de datos OLE DB y la biblioteca de plantillas OLE DB. (OLE DB no se recomienda para las aplicaciones nuevas, excepto en escenarios que implican servidores vinculados).</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    
</ul>

---

<h2>Referencia</h2>

<ul class="panelContent cardsW">
 <li>
        <a href="https://azure.microsoft.com/develop/cpp/">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardText">
                        <h3>Centro para desarrolladores de C y C++ de Microsoft Azure</h3>
                        <p>Azure facilita la compilación de aplicaciones en C++ con más flexibilidad, escalabilidad y confiabilidad, usando las herramientas que prefiera.</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="https://docs.microsoft.com/azure/storage/storage-c-plus-plus-how-to-use-blobs">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardText">
                        <h3>Cómo usar el almacenamiento de blobs de C++</h3>
                        <p>Azure Blob Storage es un servicio que almacena datos no estructurados en la nube como objetos o blobs. El almacenamiento de blobs puede almacenar cualquier tipo de texto o datos binarios, como un documento, un archivo multimedia o un instalador de aplicación. El Almacenamiento de blobs también se conoce como "almacenamiento de objetos".</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="https://docs.microsoft.com/sql/odbc/reference/odbc-programmer-s-reference">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardText">
                        <h3>Referencia del programador de ODBC</h3>
                        <p>La interfaz ODBC está diseñada para su uso con el lenguaje de programación C. El uso de la interfaz ODBC abarca tres áreas: instrucciones SQL, llamadas a funciones de ODBC y programación de C.</p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardText">
                        <h3><a href="https://www.microsoft.com/download/details.aspx?id=53339" title="Microsoft® ODBC Driver 13.1 for SQL Server® - Windows Download Page">Controlador ODBC 13.1 para SQL Server</a></h3>
                        <p>Microsoft ODBC Driver 13.1 for SQL Server es una única biblioteca de vínculos dinámicos (DLL) que incluye compatibilidad con entornos de ejecución de aplicaciones que usen API de código nativo para conectarse a Microsoft SQL Server 2008, SQL Server 2008 R2, SQL Server 2012, SQL Server 2016, Analytics Platform System, Azure SQL Database y Azure SQL Data Warehouse. Puede descargar el controlador aquí.</p>
                    </div>
                </div>
            </div>
        </div>        
    </li>
    
</ul>
