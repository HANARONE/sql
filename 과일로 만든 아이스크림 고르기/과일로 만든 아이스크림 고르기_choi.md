SELECT A.FLAVOR
    FROM FIRST_HALF A, ICECREAM_INFO B
        WHERE A.FLAVOR == B.FLAVOR
              and A.TOTAL_ORDER >= 3000
              and B.INGREDIENT_TYPE = 'fruit_based'