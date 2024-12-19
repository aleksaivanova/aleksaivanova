SELECT last_name
FROM client 
WHERE id IN (SELECT client_id
            FROM view 
            WHERE apartment_id IN (SELECT id FROM apartment
                                  WHERE rooms = 3)
            GROUP BY client_id
            HAVING COUNT(apartment_id) > 2);
