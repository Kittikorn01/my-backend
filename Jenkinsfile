pipeline {
    agent {
        docker {
            // 1. เปลี่ยนจาก alpine เป็นตัวธรรมดา (แก้ปัญหา npm crash)
            image 'node:18' 
            reuseNode true
        }
    }
    stages {
        stage('Test npm') {
            steps {
                sh 'npm --version'
                sh 'node --version'
            }
        }
        stage('Build') {
            steps {
                // 2. ใช้ npm install ธรรมดา (กันเหนียวเรื่อง package-lock)
                sh 'npm install'
                
                // 3. ลบบรรทัด 'npm run build' ทิ้งไปเลย (เพราะ Backend มักไม่ต้อง Build)
                // sh 'npm run build'  <-- ลบอันนี้ออก หรือใส่ // ไว้ข้างหน้า
            }
        }
    }
}