using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Enemies : MonoBehaviour
{
    [SerializeField] protected float speed;
    [SerializeField] protected int enemyHealth;
    [SerializeField] protected GameObject explosionEffect;
    [SerializeField] protected float waitTime;
    [SerializeField] protected GameObject shot;
    [SerializeField] protected float shotSpeed;
    [SerializeField] protected int pointsByEnemy;


    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        
    }

    public void EnemyDamage(int damage)
    {
        if (transform.position.y < 5f)
        {
            enemyHealth -= damage;
            if (enemyHealth <= 0)
            {
                Instantiate(explosionEffect, transform.position, transform.rotation);
                Destroy(gameObject);

                var generator = FindAnyObjectByType<EnemySpawner>();
                generator.ReduceEnemiesQtd();
                generator.PointsToGive(pointsByEnemy);
                
            }
        }
        
    }

    private void OnTriggerEnter2D(Collider2D other)
    {
        if (other.CompareTag("Destroyer"))
        {
            var generator = FindAnyObjectByType<EnemySpawner>();
            generator.ReduceEnemiesQtd();
            Destroy(gameObject);
        }
    }

    private void OnCollisionEnter2D(Collision2D other)
    {
        if (other.gameObject.CompareTag("Player"))
        {
            Instantiate(explosionEffect, transform.position, transform.rotation);
            Destroy(gameObject);
            other.gameObject.GetComponent<PlayerController>().PlayerDamage(1);
        }

        
    }
}
