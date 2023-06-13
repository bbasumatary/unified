# unified
Unified project


        ports:

          - containerPort: 80
            name: pgadmin
          env:

            - name: "PGADMIN_DEFAULT_PASSWORD"

              value: "pgadmin"

            - name: "PGADMIN_DEFAULT_EMAIL"

              value: "pgadmin@slb.com"

            - name: "PathPrefix"

              value: "/pgadmin"

            - name: "SCRIPT_NAME"

              value: '/pgadmin'

          volumeMounts:

            - mountPath: /PPDM_Scripts

              name: postgredb

    volumes:
      - ./unified-db/pgadmin:/var/lib/pgadmin

      PGADMIN_SERVER_JSON: '{"host": "postgres", "port": 5432, "username": "unifier", "password": "unifier", "sslmode": "prefer", "db": "unified-db"}'


apiVersion: v1 
kind: ConfigMap metadata: name: pgadmin-config data: servers.json: | { "Servers": { "1": { "Name": "PostgreSQL DB", "Group": "Servers", "Port": 5432, "Username": "postgres", "Host": "postgres.domain.com", "SSLMode": "prefer", "MaintenanceDB": "postgres" } } }