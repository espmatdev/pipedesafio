pipeline {
    agent any

    parameters {
        string(name: 'NOMBRE', description: 'Nombre del usuario')
        string(name: 'APELLIDO', description: 'Apellido del usuario')
        choice(name: 'DEPARTAMENTO', choices: ['contabilidad', 'finanzas', 'tecnologia'], description: 'Departamento del usuario')
    }

    stages {
        stage('Validar Datos de Entrada') {
            steps {
                script {
                    if (!params.NOMBRE || !params.APELLIDO) {
                        error "El nombre y apellido son obligatorios."
                    }
                }
            }
        }

        stage('Crear Usuario') {
            steps {
                script {
                    def login = "${params.NOMBRE}.${params.APELLIDO}".toLowerCase()
                    def password = UUID.randomUUID().toString().substring(0, 8)

                    sh """
                        sudo useradd -m -G ${params.DEPARTAMENTO} -s /bin/bash ${login}
                        echo "${login}:${password}" | sudo chpasswd
                        sudo chage -d 0 ${login}
                    """

                    echo "Usuario creado: ${login}"
                    echo "Password temporal: ${password}"
                }
            }
        }
    }
}
